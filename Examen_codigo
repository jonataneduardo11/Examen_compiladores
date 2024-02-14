import tkinter as tk
from ply import lex

# Definir los tokens
tokens = (
    'PALABRAS_R',
    'IDENTIFICADOR',
    'OPERADOR',
    'NUMERO',
    'SIMBOLO',
)

# Definir las reglas para los tokens
def t_PALABRAS_R(t):
    r'(area|base)'
    return t

t_IDENTIFICADOR = r'[a-zA-Z_][a-zA-Z0-9_]*'
t_OPERADOR = r'[*/=]'
t_NUMERO = r'\d+'
t_SIMBOLO = r'[()]'

# Ignorar espacios y tabulaciones
t_ignore = ' \t'

# Contador de líneas
def t_newline(t):
    r'\n+'
    t.lexer.lineno += len(t.value)

# Manejar errores
def t_error(t):
    print(f"Carácter ilegal '{t.value[0]}' en la línea {t.lineno}")
    t.lexer.skip(1)

# Crear el analizador léxico
lexer = lex.lex()

# Función para analizar el código
def analizar_codigo():
    codigo = codigo_text.get("1.0", "end-1c")
    lexer.input(codigo)
    resultados = []

    for tok in lexer:
        resultados.append((tok.type, tok.value))

    # Mostrar resultados en la nueva tabla
    for widget in resultados_frame.winfo_children():
        widget.destroy()

    # Crear una tabla para mostrar los resultados
    tabla = tk.Frame(resultados_frame, bg='white')
    tabla.grid(row=0, column=0)

    tk.Label(tabla, text="LEXEMA", bg='white').grid(row=0, column=0, padx=5, pady=5)
    tk.Label(tabla, text="PALABRA_R", bg='white').grid(row=0, column=1, padx=5, pady=5)
    tk.Label(tabla, text="IDENTIFICADOR", bg='white').grid(row=0, column=2, padx=5, pady=5)
    tk.Label(tabla, text="OPERADOR", bg='white').grid(row=0, column=3, padx=5, pady=5)
    tk.Label(tabla, text="NUMERO", bg='white').grid(row=0, column=4, padx=5, pady=5)
    tk.Label(tabla, text="SIMBOLO", bg='white').grid(row=0, column=5, padx=5, pady=5)

    # Ajustar el número de filas mostradas en la tabla
    num_filas_mostradas = min(len(resultados) + 1, 25)

    for i, resultado in enumerate(resultados, start=1):
        if i <= num_filas_mostradas:
            tk.Label(tabla, text=resultado[1], bg='white').grid(row=i, column=0, padx=40, pady=5)
            if resultado[0] == 'PALABRAS_R':
                tk.Label(tabla, text=resultado[1], bg='white').grid(row=i, column=1, padx=40, pady=5)
            elif resultado[0] == 'IDENTIFICADOR':
                tk.Label(tabla, text=resultado[1], bg='white').grid(row=i, column=2, padx=40, pady=5)
            elif resultado[0] == 'OPERADOR':
                tk.Label(tabla, text=resultado[1], bg='white').grid(row=i, column=3, padx=40, pady=5)
            elif resultado[0] == 'NUMERO':
                tk.Label(tabla, text=resultado[1], bg='white').grid(row=i, column=4, padx=40, pady=5)
            elif resultado[0] == 'SIMBOLO':
                tk.Label(tabla, text=resultado[1], bg='white').grid(row=i, column=5, padx=40, pady=5)

# Crear la interfaz gráfica
ventana_principal = tk.Tk()
ventana_principal.title("Analizador Léxico")
ventana_principal.configure(bg='lightblue')  # Cambiar el color de fondo principal

# Panel de entrada de código
panel_codigo = tk.Frame(ventana_principal, bg='lightblue')  # Cambiar el color de fondo del panel
panel_codigo.grid(row=0, column=0, padx=10, pady=10)

codigo_text = tk.Text(panel_codigo, height=35, width=60, bg='white')  # Cambiar el color de fondo del área de texto
codigo_text.insert(tk.END, "area=(base*altura)/2\njonatan eduardo aguillar gomez 07 de julio del 2002")
codigo_text.grid(row=2, column=2, padx=10, pady=10)

# Botón de análisis léxico
boton_analizar = tk.Button(panel_codigo, text="Analizar", command=analizar_codigo, bg='lightcyan')  # Cambiar el color del botón
boton_analizar.grid(row=1, column=1, pady=5)

# Panel de resultados
panel_resultados = tk.Frame(ventana_principal, bg='lightblue')  # Cambiar el color de fondo del panel
panel_resultados.grid(row=0, column=1, padx=10, pady=10)

# Frame para mostrar resultados
resultados_frame = tk.Frame(panel_resultados, bg='white')
resultados_frame.grid(row=0, column=0)

ventana_principal.mainloop()

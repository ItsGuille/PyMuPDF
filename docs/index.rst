from fpdf import FPDF
from io import BytesIO
import fitz  # PyMuPDF

# Crear un PDF
pdf = FPDF()
pdf.add_page()

# Título
pdf.set_font("Arial", 'B', 16)
pdf.cell(0, 10, 'Career Portfolio: Computer Science', ln=True, align='C')

# Sección: Carrera que deseo
pdf.set_font("Arial", 'B', 14)
pdf.cell(0, 10, 'Career I Desire', ln=True)
pdf.set_font("Arial", '', 12)
pdf.multi_cell(0, 10, (
    "I aspire to pursue a career in Computer Science. This field involves the study of computers and computational "
    "systems, including their theory, design, development, and application."
))

# Insertar imagen
pdf.image("path_to_your_image.jpg", x=10, y=pdf.get_y() + 10, w=50)

# Guardar el contenido del PDF en un búfer de bytes
pdf_buffer = BytesIO()
pdf_output = pdf.output(dest=pdf_buffer).encode('latin-1')

# Guardar el contenido del búfer en un archivo binario
with open("Career_Portfolio_CS.pdf", "wb") as f:
    f.write(pdf_output)

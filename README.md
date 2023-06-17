# receipt
from reportlab.platypus import SimpleDocTemplate,Table,Paragraph,TableStyle
from reportlab.lib import colors
from reportlab.lib.pagesizes import A4
from reportlab.lib.styles import getSampleStyleSheet
DATA=[
    ["Date","Name","Subscription","Price(Rs.)"],
    [
        "8/6/2023",
        "Full Stack Development with React And Live ",
        "Partial time",
        "10,999.00/-"
    ],
    ["8/6/2023", "Geeks Classes: Live Session","6 months","9999.00/-"],
    [ "Sub Total","","","30,000.00/-"],
    [" Discount","","","-3000.00/-"],
    [" Total","","","27000.00/-"]
]
pdf=SimpleDocTemplate("receipt.pdf",pagesizes=A4)
styles=getSampleStyleSheet()
title_style=styles["Heading1"]
title_style.alignment=1
title=Paragraph("Geeks for Geeks",title_style)
styles=TableStyle(
    [
        ("BOX",(0,0),(-1,-1),1,colors.black),
        ("GRID",(0,0),(4,4),1,colors.black),
        ("BACKGROUND",(0,0),(3,0),colors.gray),
        ("TEXTCOLOR",(0,0),(-1,0),colors.whitesmoke),
        ("ALIGN",(0,0),(-1,-1),"CENTER"),
        ("BACKGROUND",(0,1),(-1,-1),colors.beige),
    ]
)
table=Table(DATA,style=styles)
pdf.build([title,table])

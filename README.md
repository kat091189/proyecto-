# proyecto-

import discord
import random as r 
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True

bot = commands.Bot(command_prefix="!", intents=intents)

#listas
comandos = {
    "aire": "Datos acerca de la contaminacion del aire",
    "agua": "Datos acerca de la contaminacion del agua",
    "tierra": "Datos acerca de la contaminacion de la tierra",
    "trivia": "Preguntas",
    "tip": "Consejos"
}

datos_aire = [
    "La contaminación del aire contribuye a enfermedades respiratorias como asma y bronquitis.",
    "El dióxido de carbono (CO₂) es uno de los principales gases que causan el efecto invernadero.",
    "Los vehículos de motor son responsables de gran parte del smog en las ciudades.",
    "La quema de carbón y petróleo libera partículas finas que dañan los pulmones.",
    "La contaminación del aire puede reducir la expectativa de vida.",
    "La industria y fábricas emiten óxidos de nitrógeno y azufre que generan lluvia ácida.",
    "La exposición a partículas en suspensión aumenta el riesgo de ataques cardíacos.",
    "El humo de incendios forestales puede afectar la calidad del aire a cientos de kilómetros.",
    "El aire contaminado afecta el crecimiento de plantas y cultivos.",
    "La contaminación del aire también contribuye al cambio climático global."
]

datos_agua = [
    "Los desechos industriales pueden liberar metales pesados en ríos y lagos.",
    "El vertido de plásticos contamina océanos y afecta la vida marina.",
    "Los fertilizantes de la agricultura generan eutrofización en cuerpos de agua.",
    "Las aguas residuales sin tratar contaminan ríos y acuíferos.",
    "La contaminación del agua provoca enfermedades como cólera y diarrea.",
    "El petróleo derramado en el mar causa muerte masiva de peces y aves.",
    "Los detergentes y químicos domésticos alteran la composición del agua.",
    "Las microplásticos se acumulan en peces que luego consumimos.",
    "La acidificación de los océanos afecta corales y ecosistemas marinos.",
    "La escasez de agua potable está directamente relacionada con la contaminación."
]

datos_tierra = [ 
    "Los vertederos inadecuados liberan metales pesados al suelo.",
    "La deforestación provoca erosión y pérdida de nutrientes del suelo.",
    "Los pesticidas contaminan la tierra y afectan la salud humana y animal.",
    "La acumulación de residuos plásticos altera la fertilidad del suelo.",
    "La minería a cielo abierto contamina suelos cercanos con metales tóxicos.",
    "La contaminación del suelo puede filtrarse y afectar acuíferos subterráneos.",
    "Los derrames de petróleo contaminan grandes extensiones de tierra.",
    "La contaminación del suelo reduce la biodiversidad y mata microorganismos útiles.",
    "La industria química puede dejar residuos persistentes durante décadas.",
    "La contaminación de la tierra afecta la producción de alimentos y cultivos."
]

tips_s = [
    "Usa transporte público, bicicleta o camina para reducir emisiones de gases contaminantes.",
    "Reduce, reutiliza y recicla para disminuir la cantidad de basura.",
    "Evita el uso de plásticos de un solo uso como bolsas y botellas.",
    "Ahorra energía apagando luces y aparatos eléctricos que no estés usando.",
    "Consume productos locales para reducir la contaminación por transporte.",
    "No tires basura en calles, ríos o playas.",
    "Planta árboles y cuida las áreas verdes.",
    "Usa productos biodegradables y menos químicos tóxicos.",
    "Ahorra agua cerrando la llave cuando no la necesites.",
    "Participa en campañas de limpieza y educación ambiental."
]

trivia_s = trivia_s = [
    {
        "pregunta": "¿Qué problema de salud puede causar la contaminación del aire?",
        "opciones": {
            "A": "Asma y bronquitis",
            "B": "Diabetes",
            "C": "Fracturas óseas"
        },
        "respuesta": "A"
    },
    {
        "pregunta": "¿Qué gas contribuye al efecto invernadero?",
        "opciones": {
            "A": "Oxígeno (O₂)",
            "B": "Nitrógeno (N₂)",
            "C": "Dióxido de carbono (CO₂)"
        },
        "respuesta": "C"
    },
    {
        "pregunta": "¿Qué residuo afecta gravemente la vida marina?",
        "opciones": {
            "A": "Vidrio",
            "B": "Plásticos",
            "C": "Papel"
        },
        "respuesta": "B"
    },
    {
        "pregunta": "¿Qué actividad provoca eutrofización en cuerpos de agua?",
        "opciones": {
            "A": "Pesca artesanal",
            "B": "Uso de fertilizantes agrícolas",
            "C": "Navegación marítima"
        },
        "respuesta": "B"
    },
    {
        "pregunta": "¿Qué causa la deforestación en el suelo?",
        "opciones": {
            "A": "Mejora la fertilidad",
            "B": "Reduce la contaminacion",
            "C": "Provoca erosión"
        },
        "respuesta": "C"
    },
    {
        "pregunta": "¿Qué acción ayuda a reducir emisiones contaminantes?",
        "opciones": {
            "A": "Usar transponte publico o bicicleta",
            "B": "Usar mas autos",
            "C": "Quemar basura"
        },
        "respuesta": "A"
    },
    {
        "pregunta": "¿Qué problema causa el agua contaminada?",
        "opciones": {
            "A": "Colera y diarrea",
            "B": "Migraña",
            "C": "Insomnio"
        },
        "respuesta": "A"
    },
    {
        "pregunta": "¿Qué se debe evitar para reducir la contaminación?",
        "opciones": {
            "A": "Reciclar",
            "B": "Plantar árboles",
            "C": "Plásticos de un solo uso"
        },
        "respuesta": "C"
    },
    {
        "pregunta": "¿Qué efecto tiene la contaminación del suelo?",
        "opciones": {
            "A": "Aumenta la producción",
            "B": "Reduce la produccion de alimentos",
            "C": "No tiene impacto"
        },
        "respuesta": "B"
    },
    {
        "pregunta": "¿Qué contaminante puede filtrarse a acuíferos?",
        "opciones": {
            "A": "Metales pesados",
            "B": "Oxígeno",
            "C": "Vapor de agua"
        },
        "respuesta": "A"
    }
]



#verificacion 

@bot.event
async def on_ready():
    print("EcoBot está conectado")

#imprimir comandos 
@bot.command()
async def comandos_list(ctx):
    mensaje = "Comandos disponibles:"
    for clave, valor in comandos.items():
        mensaje += f"`{clave}`: {valor}\n"
    await ctx.send(mensaje)

#datos aleatorios
@bot.command()
async def aire(ctx):
    await ctx.send(r.choice(datos_aire))

@bot.command()
async def agua(ctx):
    await ctx.send(r.choice(datos_agua))

@bot.command()
async def tierra(ctx):
    await ctx.send(r.choice(datos_tierra))

#tips 
@bot.command()
async def tips(ctx):
    await ctx.send(r.choice(tips_s))

#trivia 
@bot.command()
async def trivia(ctx):
    pregunta = r.choice(trivia_s)

    texto = f" **Trivia Ambiental** \n\n"
    texto += f"**{pregunta['pregunta']}**\n\n"

    for letra, opcion in pregunta["opciones"].items():
        texto += f"{letra}) {opcion}\n"

    await ctx.send(texto)

    def check(x):
        return (
            x.author == ctx.author and
            x.channel == ctx.channel and
            x.content.upper() in ["A", "B", "C"]
        )

    try:
        mensaje = await bot.wait_for("message", check=check, timeout=30)
    except:
        await ctx.send("Tiempo agotado")
        return


    if mensaje.content.upper() == pregunta["respuesta"].upper:
        await ctx.send("¡Correcto!")
    else:
        await ctx.send(f" Incorrecto. La respuesta correcta era **{pregunta['respuesta'].upper()}**")


bot.run("TOKEN")


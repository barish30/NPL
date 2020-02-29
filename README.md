# Superbowl 2017


## tl;dr

Vamos a analizar una colección de tweets en inglés publicados durante un partido de fútbol.


## Contexto

El pasado 5 de febrero se celebró la [51ª edición de la Superbowl](https://en.wikipedia.org/wiki/Super_Bowl_LI), la gran final del campeonato de fútbol americano de la NFL. El partido enfrentó a los [New England Patriots](https://en.wikipedia.org/wiki/New_England_Patriots) (los favoritos, los de la costa este, con [Tom Brady](https://en.wikipedia.org/wiki/Tom_Brady) a la cabeza) contra los [Atlanta Falcons](https://en.wikipedia.org/wiki/Atlanta_Falcons) (los aspirantes, los del Sur, encabezados por [Matt Ryan](https://en.wikipedia.org/wiki/Matt_Ryan_(American_football))).

![](http://bandageek.com/wp-content/uploads/2017/02/patriots-vs-falcons.jpg)

Como cualquier final, el resultado *a priori* era impredecible y a un partido podía ganar cualquiera. Pero el del otro día fue un encuentro inolvidable porque comenzó con el equipo débil barriendo al favorito y con un Brady que no daba una. Al descanso, el marcador reflejaba un inesperado **3 - 28** y todo indicaba que los Falcons ganarían su primer anillo.

![](https://pbs.twimg.com/media/C38X-Z-VUAA-UAV.jpg)

Pero, en la segunda mitad, Brady resurgió... y su equipo comenzó a anotar una y otra vez... con los Falcons ko. Los Patriots consiguieron darle la vuelta al marcador y vencieron por **34 - 28** su quinta Superbowl. Brady fue elegido MVP del encuentro y aclamado como el mejor quaterback de la historia.

![](http://images.complex.com/complex/images/c_limit,w_680/f_auto,fl_lossy,pg_1,q_auto/d36dh2j3micwoszunssh/tom-brady-new-england-patriots-vince-lombardi-trophy-super-bowl-li)

Como os imaginaréis, tanto vaivén nos va a dar mucho juego a la hora de analizar un corpus de mensajes de Twitter. Durante la primera mitad, es previsible que encuentres mensajes a favor de Atlanta y burlas a New England y a sus jugadores, que no estaban muy finos. Pero al final del partido, con la remontada, las opiniones y las burlas cambiarán de sentido.

Como tanto Tom Brady como su entrenador, Bill Belichick, habían declarado públicamente sus preferencias por Donald Trump durante las elecciones a la presidencia, es muy probable que encuentres mensajes al respecto y menciones a demócratas y republicanos.

Por último, durante el *half time show* actuó Lady Gaga, que también levanta pasiones a su manera, así que es probable que haya menciones a otras *reinas* de la música y comparaciones con actuaciones pasadas.

![](http://www.billboard.com/files/styles/article_main_image/public/media/12-lady-gaga-super-bowl-feb-2017-billboard-1548.jpg)


## Los datos

El fichero `2017-superbowl-tweets.tsv` ubicado en el directorio `data/` contiene una muestra, ordenada cronológicamente, de mensajes escritos en inglés publicados antes, durante y después del partido. Todos los mensajes contienen el hashtag `#superbowl`. Hazte una copia de este fichero en el directorio `notebooks` de tu espacio personal.

El fichero es en realidad una tabla con cuatro columnas separadas por tabuladores, que contiene líneas (una por tweet) con el siguiente formato:

    id_del_tweet fecha_y_hora_de_publicación autor_del_tweet texto_del_mensaje


La siguiente celda te permite abrir el fichero para lectura y cargar los mensajes en la lista `tweets`. Modifica el código para que la ruta apunte a la copia local de tu fichero.



!gunzip ../data/2017-twitter-messages.tsv.gz
!ls -l ../data


tweets = []
RUTA = '../data/2017-twitter-messages.tsv'
for line in open(RUTA).readlines():
    tweets.append(line.split('\t'))

# en Windows, asegúrate de que abres el fichero de texto forzando la codificación para que sea Unicode
import codecs
tweets = []
RUTA = '../data/2017-twitter-messages.tsv'

with codecs.open(RUTA, "r", "utf-8") as f:
    for line in f.readlines():
        tweets.append(line.split("\t"))

ultimo_tweet = tweets[-1]
print('id =>', ultimo_tweet[0])
print('fecha =>', ultimo_tweet[1])
print('autor =>', ultimo_tweet[2])
print('texto =>', ultimo_tweet[3])





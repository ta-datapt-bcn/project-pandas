{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<img src=\"https://bit.ly/2VnXWr2\" alt=\"Ironhack Logo\" width=\"100\" align=\"right\"/>\n",
    "\n",
    "\n",
    "#   Project Ironhack Data Bootcamp\n",
    "\n",
    "OSCAR M. MONTERO\n",
    "\n",
    "*Data Part Time Barcelona Dic 2019*\n",
    "\n",
    "\n",
    "## Content\n",
    "- [Project Description](#project)\n",
    "- [Dataset](#dataset)\n",
    "- [Workflow](#workflow)\n",
    "- [Results](#results)\n",
    "\n",
    "<a name=\"project\"></a>\n",
    "\n",
    "## Project Description\n",
    "\n",
    "En este proyecto buscamos principalmente hacer un buen data cleaning de una base de datos que se nos ofrece,\n",
    "y gracias a este data cleaning ser capaces de obtener una información más depurada y precisa que nos permita\n",
    "entender mejor los datos y poder sacar conclusiones al respecto.\n",
    "\n",
    "Para ello partiremos de un file .csv, el cual importaremos y trataremos con la librería Pandas de Python, volviendo\n",
    "a exportar nuestro dataframe ya limpio a un nuevo archivo .csv.\n",
    "\n",
    "<a name=\"dataset\"></a>\n",
    "\n",
    "## Dataset\n",
    "\n",
    "El dataset que obtenemos lo descargamos de Kaggle y es un file .csv con un enorme registro de ataques de tiburón que han sucedido en el mundo, en multitud de países y a lo largo de un período no muy bien acotado. Las principales informaciones que se nos dan son el país donde se ha producido, el año, la fecha, la persona que sufrió el ataque, su sexo, edad, qué actividad estaba practicando, el tipo de lesión, si fue mortal o no, y otra serie de informaciones que nos encargaremos de ir analizando.\n",
    "\n",
    "Este archivo inicial, llamado GSAF5.csv contiene 5992 registros y 24 columnas (campos de información sobre cada ataque).\n",
    "\n",
    "<a name=\"workflow\"></a>\n",
    "\n",
    "## Workflow\n",
    "\n",
    "El principal trabajo realizado ha sido el de limpiar el dataset. Para ello hemos hecho los siguientes pasos:\n",
    "\n",
    "1) Import Libraries - Hemos importado la librería Pandas de Python gracias a la cual podremos tratar y manipular el dataset.\n",
    "\n",
    "2) Load CSV y Explore data - Hemos importado el file .csv comentado anteriormente y hemos hecho una primera inspección del tipo de información que contiene, pasándolo a un dataframe que trataremos en los siguientes pasos. Hemos hecho una exploración inicial para conocer el número de registros, informaciones que se nos dan, nombres de las columnas, y primera detección de columnas relevantes y número de valores nulos que nos encontramos.\n",
    "\n",
    "3) Explore Dataframe - Hemos hecho una exploración inicial para conocer el número de registros, informaciones que se nos dan, nombres de las columnas, y primera detección de columnas relevantes y número de valores nulos que nos encontramos. \n",
    "\n",
    "4) Data Cleaning - A partir de aquí hemos ido recorriendo cada columna y dependiendo del tipo de información que nos aportase la hemos considerado útil o no. En el caso de no ser útil o tener información díficilmente aprovechable, hemos ido eliminando del dataframe cada columna, para ir consiguiendo un dataframe más limitado y enfocado a la información que buscamos obtener. Por otro lado, en aquellas columnas que la información sí nos es útil hemos realizado un trabajo de eliminar duplicados, de corregir valores mal escritos, de corregir su formato, etc.\n",
    "\n",
    "5) Dataframe to CSV - El nuevo dataframe lo hemos delimitado para los registros que tenemos a partir de 1900, ya que antes de esa fecha la información en cuanto a fechas es muy confusa. Con las columnas que ya nos aportan realmente información hemos guardado el nuevo dataframe como data_clean y lo hemos convertido a un nuevo archivo .csv llamado data_clean.csv\n",
    "\n",
    "<a name=\"results\"></a>\n",
    "\n",
    "## Results\n",
    "\n",
    "Como complemento a los pasos comentados anteriormente y la labor de data cleaning, hemos añadido un punto final de DataFrame Análisis y Conclusiones, donde con la información filtrada y relacionada hemos llegado a las siguientes conclusiones:\n",
    "\n",
    "Desde 1900:\n",
    "- El mayor número de ataques se sitúa en Niños < 18 años y Jóvenes de 18-30 años.\n",
    "- El 47% de ataques es a personas menores de 18 años, y el 40% a personas entre 18 y 30 años.\n",
    "- La media de edad a la que se sufren los ataques es a los 27 años.\n",
    "- La edad más alta que se tiene registro de ataque de tiburón es a los 87 años.\n",
    "- La menor, a 1 año de edad.\n",
    "- El 89% de ataques se produce a Male (Hombres) y un 11% de ataques es a Female (mujeres).\n",
    "- Las 3 actividades que más ataques sufren son Surfing, Swimming y Fishing.\n",
    "- Los 3 países que más ataques tienen de tiburones son USA, Australia y South Africa\n",
    "\n",
    "<a name=\"obstacles\"></a>\n",
    "\n",
    "## Obstacles\n",
    "\n",
    "Me ha ido costando saber hasta qué punto podía conseguir mejorar el cleaning de cada columna. Me hubiera gustado por ejemplo sacar más partido de Date y Time, diferenciando por meses, o por momentos del día, pero no he conseguido saber cómo hacerlo a tiempo.\n",
    "\n",
    "Y también respecto a Year, he optado por filtrar a partir de 1900 porque era desde donde la información estaba mejor definida en este campo.\n",
    "\n",
    "También podría haber mejorado el cleaning de Country por ejemplo, ya que había algunos nombres de países que no estaban bien escritos, o que aparecían mares y océanos, o llamaban al mismo país de diferentes formas, pero tampoco he conseguido una manera de hacerlo que me diese tiempo a que me saliera y entregar.\n",
    "\n",
    "Otro punto, cuando he comparado las columnas de Case Number con Case Number.1 y Case Number.2 lo he hecho de una manera que lo he conseguido, pero creo que lo he hecho de manera muy poco eficiente con demasiados pasos.\n"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.0"
  },
  "toc": {
   "base_numbering": 1,
   "nav_menu": {},
   "number_sections": true,
   "sideBar": true,
   "skip_h1_title": false,
   "title_cell": "Table of Contents",
   "title_sidebar": "Contents",
   "toc_cell": false,
   "toc_position": {},
   "toc_section_display": true,
   "toc_window_display": false
  },
  "varInspector": {
   "cols": {
    "lenName": 16,
    "lenType": 16,
    "lenVar": 40
   },
   "kernels_config": {
    "python": {
     "delete_cmd_postfix": "",
     "delete_cmd_prefix": "del ",
     "library": "var_list.py",
     "varRefreshCmd": "print(var_dic_list())"
    },
    "r": {
     "delete_cmd_postfix": ") ",
     "delete_cmd_prefix": "rm(",
     "library": "var_list.r",
     "varRefreshCmd": "cat(var_dic_list()) "
    }
   },
   "types_to_exclude": [
    "module",
    "function",
    "builtin_function_or_method",
    "instance",
    "_Feature"
   ],
   "window_display": false
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}

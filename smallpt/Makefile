#*****************************************************************
# File:   Makefile
# Author: Adolof Muñoz
# Date:    2017
# Coms:   Ejemplo de Makefile
#         Ejecutar 'make' para compilar (o 'make -f Makefile')
#         Ejecutar 'make' clean para limpiar (borrar lo que genere)
#*****************************************************************

#---------------------------------------------------------
# macros
RM = /bin/rm -f  # para limpiar
CC = g++         # para compilar
#---------------------------------------------------------
# para compilación y enlazado ("linkado")
CPPFLAGS=-I. -I../fuentes_p3_new/ConcurrentBoundedQueue -I../fuentes_p3_new/Semaphore_V4 -I../fuentes_p3_new/Logger_V2  -I../fuentes_p3_new/BoundedQueue  -std=c++11     # opciones compilación
LDFLAGS=-pthread            # opciones de "linkado"
#---------------------------------------------------------
# vars
CBQ = ../fuentes_p3_new/ConcurrentBoundedQueue/ConcurrentBoundedQueue
BQ = ../fuentes_p3_new/BoundedQueue/BoundedQueue
SM = ../fuentes_p3_new/Semaphore_V4/Semaphore_V4
LG = ../fuentes_p3_new/Logger_V2/Logger
all: smallpt_thd smallpt_queue #lo que se generará al ejecutar "make"
#---------------------------------------------------------
# "linkar" y generar ejecutable.
smallpt_thd: smallpt_thd.o
	${CC} smallpt_thd.o -o smallpt_thd ${CPPFLAGS} ${LDFLAGS}
smallpt_queue: smallpt_queue.o ${CBQ}.hpp ${BQ}.hpp ${SM}.o ${LG}.o
	${CC} smallpt_queue.o ${SM}.o ${LG}.o -o smallpt_queue ${CPPFLAGS} ${LDFLAGS}
#---------------------------------------------------------
%.o: %.cc
	${CC} ${CPPFLAGS} -Wall -c $<
#---------------------------------------------------------
# Cuidado con lo que se pone aquí, que se borra sin preguntar
clean:
	$(RM) *.o core smallpt_thd smallpt_queue ${SM}.o ${LG}.o

cmake_minimum_required(VERSION 3.0)

#Comentarios em Cmake sao representados pela cerquilha

project(CriandoBibliotecaComExecutavel) #Nome do projeto

#Cria variaveis que serao usadas no decorrer do projeto
set(EXECUTAVEL_PATH     ${CMAKE_SOURCE_DIR}/executavel)
set(LIB_AMERICA_PATH    ${CMAKE_SOURCE_DIR}/libAmerica)

#GLOB feito para pegar arquivos das bibliotecas
file(GLOB LIB_AMERICA_HEADERS ${LIB_AMERICA_PATH}/inc/*.h)
file(GLOB LIB_AMERICA_SOURCES ${LIB_AMERICA_PATH}/src/*.c)

#Pega todo os arquivos no formato .h e salva na variavel EXEC_HEADERS
file(GLOB EXEC_SOURCES ${EXECUTAVEL_PATH}/src/*.c)

#Cria Biblioteca chamada libAmerica e vincula com os Headers e Sources
add_library(libAmerica ${LIB_AMERICA_HEADERS} ${LIB_AMERICA_SOURCES})

#Usado para especificar os diret�rios de header.
#O primeiro par�metro � o alvo (no caso, a biblioteca libAmerica)
#O segundo (e opcional) � o especificador de visibilidade. PRIVATE � usado apenas para o alvo atual e o PUBLIC permite o acesso para qualquer alvo.
#Ap�s a defini��o (ou n�o) do especificador, temos os diret�rios dos headers)
target_include_directories(libAmerica PUBLIC ${LIB_AMERICA_PATH}/inc)

#Cria o Execut�vel com os respectivos sources (nesse projeto, apenas o arquivo executavel.c est� sendo usado)
add_executable(appExecutavel ${EXEC_SOURCES})

#Linka o appExecutavel com as bibliotecas usadas no projeto (no caso, apenas a libAmerica)
target_link_libraries(appExecutavel libAmerica)

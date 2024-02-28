# Cerquilha/Hashtag sao a forma de criar comentario no CMake
cmake_minimum_required(VERSION 3.0)

#nomeDoProjeto
project(NomeDoProjeto)

#Cria o executavel. O primeiro parametro é o nome e o segundo em diante são os arquivos (ou variaveis que contem os arquivos)
#Será criado um executável chamado NomeDoExecutavel
add_executable(NomeDoExecutavel
				helloWorld.c)
# ------------------------------------------------- -----------------------
#
# Copyright 2017 WSO2, Inc. (http://wso2.com)
#
# Licenciado sob a Licença Apache, Versão 2.0 (a "Licença");
# você não pode usar este arquivo, exceto em conformidade com a Licença.
# Você pode obter uma cópia da Licença em
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# A menos que exigido pela lei aplicável ou acordado por escrito, o software
# distribuído sob a Licença é distribuído em uma base "COMO ESTÁ",
# SEM GARANTIAS OU CONDIÇÕES DE QUALQUER TIPO, expressas ou implícitas.
# Veja a Licença para o idioma específico que governa as permissões e
# limitações sob a licença
#
# ------------------------------------------------- -----------------------

# set to product base image
FROM wso2ei-base:6.1.1

# expose integrator ports
EXPOSE 8280 8243 9443

# set entrypoint to integrator startup script
CMD "${WSO2_SERVER_HOME}/bin/integrator.sh"

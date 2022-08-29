To deploy Kubernetes manually;

The Values.yaml File contains Deployment and Service. We revise it according to our own system. We give the information of our repo to Containers in Deployment.

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Environment variable	Description
ACCEPT_EULA	Set the ACCEPT_EULA variable to any value to confirm your acceptance of the End-User Licensing Agreement. Required setting for the SQL Server image.

MSSQL_PID	Set the SQL Server edition or product key. Possible values include:

Evaluation
Developer
Express
Web
Standard
Enterprise
A product key



-------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Install Command;

kubectl create ns mssql

helm upgrade --install mssql . --set ACCEPT_EULA.value=Y --set MSSQL_PID.value=Developer -n mssql


-------------------------------------------------------------------------------------------------------------------------------------------------------------------------


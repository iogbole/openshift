# Openshift cluster monitoring 


`oc whoami`

Login as system admin
`oc login -u system:admin`
 
List projects. There are many more projects available for the admin account
oc get projects

Create a new project with the name 'appdynamics'
`oc new-project appdynamics --display-name="AppDynamics"`
 
## Make sure that appdynamics is the active project:
`oc project appdynamics`

# Security

RBAC governs access users to resources in Kubernetes and OpenShift. 

The key RBAC entities are Users, Service Accounts, Roles, ClusterRoles, RoleBindings and ClusterRoleBinding. In the nutshell, you define users, roles and then connect users to roles through rolebindings.

More on RBAC https://kubernetes.io/docs/reference/access-authn-authz/rbac/

OpenShift provides several utilities that make the setup easier.

While in appdynamics account, let's add view/edit rights to the project for the 'developer' user.



Grant developer access to appdynamics project
`oc policy add-role-to-user view developer`
`oc policy add-role-to-user edit developer`


Login as user "developer".
Now you should see a list with two projects that user 'developer' has access to.

`oc login -u developer`

Make sure to make appd active:
`oc project appdynamics`
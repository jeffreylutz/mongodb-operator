# k8s_mongodb

Pre-req
- kubectl:  Be able to run against a kubernetes cluster

Instructions
- cd into the 1-operator directory and run:  **./init-environment**
   RUN:  **watch kubectl -n mongodb get pods**
         Wait for the operator to fully start and STATUS reports Running

- cd into the 2-ops-manager directory and run: **./init-environment**
   RUN:  **watch kubectl -n mongodb get pods**
         Wait for the ops-manager pods to report Running status
   RUN:  **kubectl -n mongodb get om**
         Wait for APPDB and OPSMANAGER status to be Running

- Run **kubectl port-forward ops-manager-0 8080**
      Then connect via a browser:  http://localhost:8080
      login:   admin / Password123!
      Navigate to the **Access Manager -> Settings** area and copy the organization ID

- cd into the 3-mongodb directory and run: **./init-environment**
      Paste the org id into:  3-mongodb/dev/kustomization.yaml file where orgId=

    From within 3-mongodb run:  **./init-environment**
      Watch the **kubectl -n mongodb get pods** and please
      note the "my-standalone-0" pod attempting to start.  

     The problem is that the "my-standalone-0" pod doesn't go beyond **Init** status.

     What is issue with starting mongodb pods?

# pv_pvc_to_docker-registry

    cat > pv.yml  :- copy the code from archietecture doc 
    vi pv.yml :- paste the path and server i.e server ip which is of services.lab.com
    oc create -f pv.yml 
    11  oc get pv
    cat > pvc.yml :- copy the copy or do through commands
    vi pvc.yml 
    oc create -f pvc.yml 
    oc get pv,pvc :- check if they bound
    oc get dc
    oc edit dc docker-registry :- edit vloume claim name (pvc name)
          In DC of Docker-registry you go to the volumes and remove the empty dir from there and below the name type
            - name: docker-volumes
              persistentVolumeClaim:
                claimName: mypvc
	  #oc set volumes dc/docker-registry --name=registry-storage --add --overwrite -t pvc --claim-name=internal_pvc --claim-mode=RWM --claim-size=5Gi
    oc get pods -w
    oc get pods

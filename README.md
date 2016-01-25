# eclipse-mars
eclipse mars image (test)

#usage au bureau
#test avec git
#idéalement, git devrait être dispo dans l'image. À revoir...

#docker create -v /gitworkspace --name gitworkspace lemaypy/volume-git /bin/true
#docker create -v /eclipseworkspace --name eclipseworkspace lemaypy/volume-eclipse /bin/true
JOB=$(docker run -d --name git test/git /bin/sh -c "while true; do echo Hello world; sleep 1; done")
docker run --rm --name=eclipse-mars --volumes-from=eclipseworkspace --volumes-from=gitworkspace --link git:git -e DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:ro  lemaypy/eclipse-mars


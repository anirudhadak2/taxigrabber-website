# taxigrabber-website



step 1 :  install jenkins on ubuntu killercode and take dashboard access 

              create user jenkins and account anirudha
            
                after installation 


step2:  got to the

         Dashboard  > Manage Jenkins >  Plugins 
         
           Available Plugins  :    Docker 1.4
                                               Docker Commons 
                                               
                                               Docker API   3.3.1
                                               
                                               docker-build-step 2.9
                                               
                                               CloudBees  Docker Build and Publish 1.4.0 
                                               
                 install this plugins 

----------------------------------------------------------------------------

 Step 3 :   Dashboard > Manage Jenkins > Credentials   >  System  > Global Credential (Unrestricted) > add new
 
                  New Credentials
                  
                   kind  : Username with Password 
                   
                  Scope: Global(jenkins,nodes,items,all child items ,etc)

                 Username: anirudhadak2 (dockerhub username)
                 
                 Password: AP@2772000

                 ID  :  dockerhub

                 
 ----------------------------------
-----------------------------------------------------------------

create new  porject test1    for  docker image  on node 
     dockerfile build and  run  on the docker 


Dashboard :  new item :  test1  =  freeStyle Project

Dashboard >  test1  >  Configuration


Configure :   General  :  Description :  test1 for docker image on jenkins push to the dockerhub

                   
            Source Code  Management : Git
            
                                            Repositories
                                            
                                            Repositories URL : https://github.com/anirudhadak2/taxigrabber-website.git
                                            
                                            Credentials: none
                                            
                                        Branch to build
                                        
                                           */master

    -------------------------------------------------------------------                                       

              Build  Triggers :
                                        poll SCM
                                        
                                            schedule: */1 * * * *

                

               build steps :     Execute shell
                                 Command 
                                # Download the buildx binary
                                
   mkdir -p ~/.docker/cli-plugins
   
   curl -SL https://github.com/docker/buildx/releases/download/v0.6.3/buildx-v0.6.3.linux-amd64 -o ~/.docker/cli-plugins/docker-buildx
   
  # Make it executable
  
  chmod a+x ~/.docker/cli-plugins/docker-buildx
  
  docker build  -t  taxi-graber  . 
  
  docker run -p 28080:80 --name  taxi  -d  taxi-graber
  
  docker ps

                          
                            [Save]     [Apply]

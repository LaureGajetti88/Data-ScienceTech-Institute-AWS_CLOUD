**************************************************************************************** PART I **************************************************************************************

1. Create a server with anaconda to open a jupiter notebook
2. Run the code extract on https://github.com/leodsti/AWS_Tutorials name : 00-mnist-cnn

****************************************************************************************************************************************************************************************************

1. As last tutorial : Login on rosetta, then "go to consol AWS"

IMPORTANTE NOTE : To do this tutorial we clone a git repertory source on : https://github.com/leodsti/AWS_Tutorials

1. Create an instance EC2 :

   1. **Ubuntu Server 18.04 LTS (HVM), SSD Volume Type** - ami-08d658f84a6d84a80 (64 bits x86) / ami-047d41821c231284a (64 bits Arm)
   2. Use a large disk : t2.2xlarge (i took 20G in configuration storage)
   3. Use a already configured VPC if you have 
   4. Use your subnet (public with all the connexion if you have) instead, create your subnet with input access to log on your server
   5. Enable automatic adress ip

   Click on next, until add tag : 

   For storage configuration, use 20G.

   2. Choose a name (good practice)
      1. I choose : "Project S19 Jupiter Notebook"

   Click on next, configure subnet and add existing if you have, instead add rule you need

   Lauch your instance (use your key if you have or create them and don't forgot to dowload them!!)

   

   3. Then we connect on you terminal to the instance : 

      1. Click on connect (after selected the instance do you want) and keep the ssh :

         ```
         ssh -i "S19KeyPairAWS.pem" ubuntu@ec2-63-35-190-174.eu-west-1.compute.amazonaws.com
         ```

      2. Confirm "yes"

      3. Now execute this commande on terminal :

         ```
         $wget https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh
         
         $sudo bash Anaconda3-2019.03-Linux-x86_64.sh #Answer yes to all questions 
         
         #If conda command is not found after installation
         # It my path correct it your is different 
         $ export PATH=~/home/ubuntu/anaconda3/bin:$PATH
         
         $source ~/.bashrc
         
         # check your version 
         $python --version # a have Python 3.7.3
         
         
         $conda update conda
         $conda update anaconda
         $conda update python
         $conda update --all
         
         $conda create --name tf-lolo
         $source activate tf-lolo
         $conda install tensorflow-gpu
         $conda install ipykernel jupyter
         
         $python -m ipykernel install --user --name tf-lolo --display-name "TensorFlow-GPU"
         
         $conda install keras-gpu
         $conda install opencv
         
         #For the Application Server installation
         #I recommend using an Ubuntu AMI
         $git clone https://github.com/leodsti/AWS_Tutorials.git
         $cd AWS_Tutorials/MNIST/
         ```

         tf-lolo is my proper name that i want you can change it.

         

      4. Now : command to launch Jupiter notebook : 

         ```
         $jupyter notebook --ip=0.0.0.0 --no-browser
         ```

      5. Now how to connect on the yter interface

         1. Open a browser like google : 

         2. keep on your instance the public ip4 : me it's : 34.245.218.134

         3. In the https : copie and past : 34.245.218.134 and concatenate with token that give you when you execute the last command you have something like : 

            ```
                To access the notebook, open this file in a browser:
                    file:///run/user/1000/jupyter/nbserver-4200-open.html
                Or copy and paste one of these URLs:
                    http://(ip-192-168-1-126 or 127.0.0.1):8888/?token=125bf4d3fc81331b1e197490fc60fe771c4f69989e1e16a9
            ```

            you keep : `:8888/?token=125bf4d3fc81331b1e197490fc60fe771c4f69989e1e16a9` it's your token so the complete adress : 

            `34.245.218.134:8888/?token=125bf4d3fc81331b1e197490fc60fe771c4f69989e1e16a9`

      6. Remark : we can do installation more concatenate : like :

         1. Upload the file requirements.txt on the serveur : 

            ```
            absl-py==0.7.1
            astor==0.8.0
            Click==7.0
            Flask==1.0.3
            gast==0.2.2
            grpcio==1.21.1
            h5py==2.9.0
            imageio==2.5.0
            imread==0.7.1
            itsdangerous==1.1.0
            Jinja2==2.10.1
            Keras==2.2.4
            Keras-Applications==1.0.8
            Keras-Preprocessing==1.1.0
            Markdown==3.1.1
            MarkupSafe==1.1.1
            numpy==1.16.4
            Pillow==6.0.0
            protobuf==3.8.0
            PyYAML==5.1.1
            scipy==1.3.0
            six==1.12.0
            tensorboard==1.9.0
            tensorflow==1.9.0
            termcolor==1.1.0
            virtualenv==16.6.0
            Werkzeug==0.15.4
            ```

            Then on your terminal execute : `pip3 install -r requirements.txt`

         2. If not work , execute line by line to search which package don't work :

            1. For me, imread don't work so i execute : 

            ```
            conda install -c https://conda.binstar.org/luispedro imread
            ```

            Now to install 'flask' i have to update conda (as the terminal advertize me ). But i have a permission denied to update conda so first, give permission to your user (me : ubuntu) then update commande conda, then, install flask 

            ```
            $sudo chown -R ubuntu anaconda3
            
            $conda update -n base -c defaults conda
            
            $conda install tensorflow==1.9.0
            
            $conda install Flask==1.0.3
            ```

         

         

         ****************************************************************************************** PART II **************************************************************************************

         1. Source also :  https://github.com/leodsti/AWS_Tutorials 
         2. 

         ------

         

      
---
title: "Downloading the Lossless Pipeline"
teaching: 35
exercises: 10
questions:
- "How do we download and set up the Lossless pipeline?"
objectives:
- "Setting up the Lossless pipeline to prepare for submitting jobs."
keypoints:
- "Ensure the pipeline is set up on both the **local** and **remote** machine."
- "Remember to always pay attention to whether you are running a bash command on your **local** machine versus the **remote** computer cluster."
---

## Download/Setup the pipeline (local)

1. In the terminal, navigate to the root of your project (this will be the Face13 folder):

    ```bash
    >> cd path/to/project/directory/Face13
    ```

    > ## Creating Project Folder
    > If you have not yet created your project folder (Face13 for the tutorial) or initalized your data, you should begin with the [BIDS-EEG-EEGLAB tutorial](https://carpentries-incubator.github.io/SDC-BIDS-EEG-EEGLAB/).
    >
    > {: .source}
    {: .callout}

    > ## Running Your Own Data- Project Name
    > If you are running your own data you will have a different project name than Face13. Throughout this tutorial, replace Face13 with your own project name.
    >
    > {: .source}
    {: .checklist}

2. If there is not already a derivatives folder within your project folder, create a derivatives folder:

    ```bash
    >> mkdir derivatives
    ```

3. Change directory into the derivatives folder:
    
    ```bash
    >> cd derivatives
    ```

4. Within the derivatives folder, clone/download the pipeline repository. **NOTE:** Use the recursive flag in order to clone all the required submodules:

    ```bash
    >> git clone --recursive https://github.com/BUCANL/EEG-IP-L.git
    ```

## Download/Setup the pipeline (remote)

1. Open a new terminal window and log into Graham, replacing [user_name] with your Graham username:

    ```bash
    >> ssh [user_name]@graham.computecanada.ca
    ```

2. Navigate to the location where you want to download the pipeline onto the remote cluster, replacing [user_name] with your Graham username:

    ```bash
	>> cd /scratch/[user_name]
    ```

3. Create a project folder (we will call it 'Face13' here):

    ```bash
    >> mkdir Face13
    ```

4. Change directory into the Face13 folder:

    ```bash
    >> cd Face13
    ```

5. In the Face13 folder, create a derivatives folder: 

    ```bash
    >> mkdir derivatives
    ```

6. Change directory into the derivatives folder:

    ```bash
    >> cd derivatives
    ```

7. Within the derivatives folder, clone/download the pipeline repository. **NOTE:** Use the recursive flag in order to clone all the required submodules:

    ```bash
    >> git clone --recursive https://github.com/BUCANL/EEG-IP-L.git
    ```

## Remote setup

If you are starting a new study, this process will need to be repeated. However, the Octave package installation will typically proceed much quicker if the new study is being run on the same account. 

1. Navigate to the folder that contains your octave packages. Note that if this is your first time running the EEG-IP-L pipeline, you will not have an octave folder until after you run the Setup Remote script and you can skip forward to Step 3.

    ```bash
    >> cd ~/octave
    ```

2. Check if any of the following are in your octave directory: IO, Signal, Struct, Control, Parallel. Remove these directories if they are present.

3. Navigate back to the root of your **remote** project folder, replacing [user_name] with your own username and [project_name] with your project name (the project name for the tutorial is `Face13`):

    ```bash
    >> cd /scratch/[user_name]/[project_name]
    ```

4. Run the remote setup script and follow the on screen prompts:

    ```bash
    >> bash derivatives/EEG-IP-L/code/install/setup-remote.sh
    ```

> ## Errors with Setup Remote 
> If the `setup-remote.sh` procedure fails, or needs to be rerun for any reason, the **lock** files must be removed. These files prevent portions of the `setup-remote.sh` procedure from being run. An important distinction is that these files are created upon success **or** failure. This means that if something has gone wrong during the process, the lock files will need to be removed or `setup-remote.sh` will skip that section of the procedure. Below are the bash commands to remove the four lock files that are created. These commands are meant to be run from the project root on the remote.
>
> ```bash
> >> rm derivatives/EEG-IP-L/code/misc/locks/amica-make.lock
> >> rm derivatives/EEG-IP-L/code/misc/locks/executable-files.lock
> >> rm derivatives/EEG-IP-L/code/misc/locks/fieldtrip-made.lock
> >> rm derivatives/EEG-IP-L/code/misc/locks/octave-pkgs.lock
> ```
>
>{: .source}
{: .callout}


{% include links.md %}

---

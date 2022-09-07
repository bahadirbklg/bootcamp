# GCP’de Kubernetes cluster kurulumu 

(*Batur*) Bahadir Bakkaloglu 

this file created as .docx . I wasn't planning to publish this on public. At first i thought it as we will mailto some adrees

 for now i used docx to md converter. That is why it is very unordered. it'll be fixed soon


**Credits :** I’ll apply the instructions from[ HashiCorp Learn’s Repository](https://github.com/hashicorp/learn-terraform-provision-gke-cluster) with small *tweaks*

After gcloud auth procedure

We will want to determine our variables

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.001.png)![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.002.png)




To use terraform there should be initialization step to set up terraform files to our repository:

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.004.png)




As we apply .tf scripts takes its instructions to set up infrastructure on GKE as requested.

Here is modules that it will create for us :

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.005.png)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.006.png)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.007.png)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.008.png)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.009.png)

Of course we will want give it a chunky yes:

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.010.png)

Things happen.. You know

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.011.png)

Here is quick fix

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.012.png)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.013.png)

Hit enter harder and it wont happen again(just joking)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.014.png)


Apparently it can, even when you push buttons harder..

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.015.png)

[This ](https://cloud.google.com/migrate/containers/docs/config-dev-env)document on gke gave me that command : 

gcloud services enable servicemanagement.googleapis.com servicecontrol.googleapis.com cloudresourcemanager.googleapis.com compute.googleapis.com container.googleapis.com containerregistry.googleapis.com cloudbuild.googleapis.com

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.016.png)

Let’s be gentle about clicking enter this time

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.017.png)


✨💫 And that worked  \(★ω★)/ 💫✨

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.018.png)



Lets check on gcloud console

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.019.png)

⚡🇮‌🇹‌🇸‌ 🇦‌🇱‌🇮‌🇻‌🇪‌⚡

*Attention :*

` `*Hitting enter hard or gentle does not provide any benefits. I assume this is can be correlated to [this](https://www.youtube.com/watch?v=8AzjDs8aF7g) idea*



Extra :

I know we have reached our milestone but I want to continue Hashicorp learns instructions. Because it looks fun!

i ‘ll deploy kubernetes dashboard

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.020.png)

We will apply [recommended.yaml](https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta8/aio/deploy/recommended.yaml)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.021.png)

Deprecation warnings scares me but let’s move on

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.022.png)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.023.png)

Declarative feels like magic you say the magic\* words then boom

We will need administrative user for k8

Hashicorps seems like already have a solution

[Kubernetes-dashboard-admin.yaml](https://raw.githubusercontent.com/hashicorp/learn-terraform-provision-gke-cluster/main/kubernetes-dashboard-admin.rbac.yaml) (it basically creates an admin user) 

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.024.png)

And theres still deprecation warnings. I’ll ignore for now


![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.025.png)

It’s so cool . but i didn’t understand how node names written twice





Kubernetes üzerine MySQL kurulumu + doküman hazırlanması

\3. Kubernetes üzerine WordPress kurulumu + otomatik ayarlar

I was experimenting on vm following [this](https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/) now its time for ingress and using StatefulSet I believe we can achieve HA 


![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.026.png)






I wanted to try helm so :

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.027.png)

That was easy. But researching period was not..


Now we can scale primary mysql pod

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.028.png)

Stateful replicas will scale gradually (one-by-one) as *feature*

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.029.png)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.030.png)



Scale has taken it’s place. They restarted (for a reason of scaling i guess ?)

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.031.png)


why 

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.032.png)


Oops.. 

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.033.png)


Something is unreliable and i dont want unreliable gcp..



Backup plan !

![](Aspose.Words.cc6bb587-f2cd-46b4-a13c-60895ac7cabe.034.png)


#and i'm sorry to time is up to submit project i'll make it properly next time ...
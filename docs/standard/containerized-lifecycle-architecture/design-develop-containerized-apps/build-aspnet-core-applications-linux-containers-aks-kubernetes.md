---
title: AKS/Kubernetes kümeler halinde Linux kapsayıcıları olarak dağıtılan bir ASP.NET Core 2.2 uygulamalar oluşturun
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: 28d2f557e4434ef7e5c2c3f8d17d6d3d6a80ce2a
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452779"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="4eb4e-103">Linux kapsayıcıları olarak dağıtılan bir AKS/Kubernetes orchestrator içinde ASP.NET Core 2.2 uygulamalar oluşturun</span><span class="sxs-lookup"><span data-stu-id="4eb4e-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="4eb4e-104">Azure Kubernetes Hizmetleri (AKS), kapsayıcı dağıtımı ve Yönetimi basitleştirin Azure'nın yönetilen Kubernetes düzenlemeleri hizmetleridir.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="4eb4e-105">AKS ana özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4eb4e-105">AKS main features are:</span></span>

- <span data-ttu-id="4eb4e-106">Azure'da barındırılan denetim düzlemi</span><span class="sxs-lookup"><span data-stu-id="4eb4e-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="4eb4e-107">Otomatik yükseltme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-107">Automated upgrades</span></span>
- <span data-ttu-id="4eb4e-108">Kendi kendine iyileştirme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-108">Self-healing</span></span>
- <span data-ttu-id="4eb4e-109">Kullanıcı yapılandırılabilir ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-109">User configurable scaling</span></span>
- <span data-ttu-id="4eb4e-110">Hem geliştiriciler hem de küme operatörleri için basit bir kullanıcı deneyimi.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="4eb4e-111">Aşağıdaki örnekler, Linux üzerinde çalışan ve geliştirme işlemi sırasında bir AKS kümesi, azure'da dağıtır bir ASP.NET Core 2.2 uygulama oluşturulmasını keşfedin. Visual Studio 2017'yi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="4eb4e-112">Visual Studio 2017'yi kullanarak ASP.NET Core 2.2 projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4eb4e-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="4eb4e-113">ASP.NET Core, Microsoft ve GitHub üzerinde .NET topluluk tarafından korunan bir genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="4eb4e-114">Bu Windows, macOS ve Linux'ta destekleyen platformlar arası ve cihaz, Bulut ve katıştırılmış IOT senaryoları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="4eb4e-115">Bu örnek, örnek oluşturmak için ek bilgisine ihtiyacınız yoktur, bir Visual Studio Web API şablonu temel alan basit bir proje kullanır.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="4eb4e-116">Bir ASP.NET Core 2.2 teknolojisini kullanarak REST API'sini küçük bir proje çalıştırmak için tüm öğeleri içeren bir standart şablonu kullanarak proje oluşturmak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Yeni Proje penceresinin Visual Studio kullanarak ASP.NET Core Web uygulaması seçme ekleyin.](media/create-aspnet-core-application.png)

<span data-ttu-id="4eb4e-118">**Şekil 4-36**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-118">**Figure 4-36**.</span></span> <span data-ttu-id="4eb4e-119">ASP.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="4eb4e-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="4eb4e-120">Visual Studio'da örnek proje oluşturmak için seçin **dosya** > **yeni** > **proje**seçin **Web**proje türleri ardından sol bölmedeki **ASP.NET Core Web uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="4eb4e-121">Visual Studio web projeleri için şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="4eb4e-122">Bizim örneğimizde, seçin **API** bir ASP.NET Web API uygulaması oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="4eb4e-123">Çerçeve ASP.NET Core 2.2 seçtiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="4eb4e-124">.NET core 2.2 en son Visual Studio 2017 sürümünde bulunan ve otomatik olarak yüklenir ve Visual Studio 2017'yi yüklediğinizde sizin için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![API seçeneği belirlenmiş bir ASP.NET Core Web uygulaması türünü seçmek için visual Studio iletişim.](media/create-web-api-application.png)

<span data-ttu-id="4eb4e-126">**Şekil 4-37**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-126">**Figure 4-37**.</span></span> <span data-ttu-id="4eb4e-127">ASP.NET CORE 2.2 seçme ve Web API proje türü</span><span class="sxs-lookup"><span data-stu-id="4eb4e-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="4eb4e-128">.NET Core herhangi bir önceki sürümü varsa, indirin ve yükleyin 2.2 sürümünden <https://www.microsoft.com/net/download/core#/sdk>.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="4eb4e-129">Docker desteği projeyi oluştururken ekleyebilir veya daha sonra bu nedenle, "projenizin herhangi bir zamanda docker kapsayıcılarında çalıştırın".</span><span class="sxs-lookup"><span data-stu-id="4eb4e-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="4eb4e-130">Proje oluşturulduktan sonra Docker desteği eklemek için Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve seçin **Ekle** > **Docker desteği** bağlam menüsünde.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Mevcut bir projeye Docker desteği eklemek için bağlam menüsü seçeneği: (Proje) sağ tıklayın > Ekle > Docker desteği.](media/add-docker-support-to-project.png)

<span data-ttu-id="4eb4e-132">**Şekil 4-38**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-132">**Figure 4-38**.</span></span> <span data-ttu-id="4eb4e-133">Var olan bir projeye Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="4eb4e-134">Docker destek eklemeyi tamamlamak için Windows veya Linux seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="4eb4e-135">Bu örnekte **Linux**, çünkü AKS Windows kapsayıcıları (olarak, geç 2018) desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Hedef işletim sistemi için bir Dockerfile seçin iletişim seçeneği.](media/select-linux-docker-support.png)

<span data-ttu-id="4eb4e-137">**Şekil 4-39**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-137">**Figure 4-39**.</span></span> <span data-ttu-id="4eb4e-138">Linux kapsayıcıları seçme.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-138">Selecting Linux containers.</span></span>

<span data-ttu-id="4eb4e-139">Bu basit adımları uygulayarak bir Linux kapsayıcısı üzerinde çalışan ASP.NET Core 2.2 uygulamanızı sahip.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="4eb4e-140">Gördüğünüz gibi Visual Studio 2017 ile Docker arasında tümleştirme için geliştirici üretkenliği tamamen yönlendirilmiş demektir.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="4eb4e-141">Uygulamanız ile çalıştırabileceğiniz artık **F5** kullanarak veya anahtar **Play** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="4eb4e-142">Proje çalıştırdıktan sonra kullanarak görüntüleri listeleyebilirsiniz `docker images` komutu.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="4eb4e-143">Görmelisiniz `mssampleapplication` Projemizin Visual Studio 2017 ile otomatik dağıtımı tarafından oluşturulmuş görüntü.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Konsol docker görüntüleri komuttan çıkış ile gösterilir: Depo, etiket, görüntü kimliği, oluşturulan (tarih) ve boyutu.](media/docker-images-command.png)

<span data-ttu-id="4eb4e-145">**Şekil 4-40**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-145">**Figure 4-40**.</span></span> <span data-ttu-id="4eb4e-146">Docker görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="4eb4e-147">Azure kapsayıcı kayıt defterinde çözümü</span><span class="sxs-lookup"><span data-stu-id="4eb4e-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="4eb4e-148">Resim gibi herhangi bir Docker kayıt defterine yükleyin [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) ya da Docker Hub, AKS kümeye, kayıt defterinden görüntüleri dağıtılacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="4eb4e-149">Bu durumda, biz görüntü Azure Container Registry'ye yükleme.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="4eb4e-150">Yayın modunda görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="4eb4e-150">Create the image in Release mode</span></span>

<span data-ttu-id="4eb4e-151">Görüntüde artık oluşturacağız **yayın** için değiştirerek modu (üretim için hazır) **yayın**gösterildiği Şekil 4-41 ve önce yaptığımız gibi uygulamayı çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Yayın modunda oluşturmak için VS araç seçeneği.](media/select-release-mode.png)

<span data-ttu-id="4eb4e-153">**Şekil 4-41**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-153">**Figure 4-41**.</span></span> <span data-ttu-id="4eb4e-154">Sürüm modu seçme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-154">Selecting Release Mode</span></span>

<span data-ttu-id="4eb4e-155">Yürütüyorsa `docker image` komutu, oluşturulan her iki görüntüleri için bir tane göreceksiniz `debug` diğeri `release` modu.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="4eb4e-156">Yeni bir etiket oluşturmak için görüntü</span><span class="sxs-lookup"><span data-stu-id="4eb4e-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="4eb4e-157">Her kapsayıcı görüntüsü ile etiketlenmesi gerekir `loginServer` kayıt defteri adı.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="4eb4e-158">Bu etiket, görüntü kayıt defterine kapsayıcı görüntüleri gönderirken yönlendirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="4eb4e-159">Görüntüleyebileceğiniz `loginServer` ad Azure portalı, Azure Container Registry'den bilgileri alma</span><span class="sxs-lookup"><span data-stu-id="4eb4e-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Sağ üst kısımdaki tarayıcı görünümü, Azure kapsayıcı kayıt defteri adı.](media/loginServer-name.png)

<span data-ttu-id="4eb4e-161">**Şekil 4-42**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-161">**Figure 4-42**.</span></span> <span data-ttu-id="4eb4e-162">Kayıt defteri adını görüntüle</span><span class="sxs-lookup"><span data-stu-id="4eb4e-162">View of the name of the Registry</span></span>

<span data-ttu-id="4eb4e-163">Veya aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="4eb4e-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan çıkış konsol.](media/az-cli-loginServer-name.png)

<span data-ttu-id="4eb4e-165">**Şekil 4-43**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-165">**Figure 4-43**.</span></span> <span data-ttu-id="4eb4e-166">PowerShell kullanarak kayıt defteri adını alın</span><span class="sxs-lookup"><span data-stu-id="4eb4e-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="4eb4e-167">Her iki durumda da adı elde.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="4eb4e-168">Bizim örneğimizde `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="4eb4e-169">Artık, görüntünün en son görüntü (sürüm görüntü) alma komutu ile etiketleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4eb4e-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="4eb4e-170">Çalıştırdıktan sonra `docker tag` komutu, görüntülerle listesi `docker images` komut ve yeni etiket görüntüsüyle görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Docker görüntüleri komuttan çıkış konsol.](media/tagged-docker-images-list.png)

<span data-ttu-id="4eb4e-172">**Şekil 4-44**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-172">**Figure 4-44**.</span></span> <span data-ttu-id="4eb4e-173">Etiketli Görüntü görüntüle</span><span class="sxs-lookup"><span data-stu-id="4eb4e-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="4eb4e-174">Azure ACR görüntü gönderme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="4eb4e-175">Azure Container Registry'ye oturum açın</span><span class="sxs-lookup"><span data-stu-id="4eb4e-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="4eb4e-176">Aşağıdaki komutu kullanarak Azure ACR görüntüyü gönderin:</span><span class="sxs-lookup"><span data-stu-id="4eb4e-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="4eb4e-177">Bu komut biraz uzun sürebilir. görüntü karşıya ancak işlem sırasında geri bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Konsol çıktısı docker itme komutundan: her katman için bir karakter tabanlı bir ilerleme çubuğu gösterir.](media/uploading-image-to-acr.png)

<span data-ttu-id="4eb4e-179">**Şekil 4-45**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-179">**Figure 4-45**.</span></span> <span data-ttu-id="4eb4e-180">Görüntüyü ACR'ye yükleme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="4eb4e-181">İşlem tamamlandığında almalısınız sonucu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4eb4e-181">You can see below the result you should get when the process completes:</span></span>

![Docker push komutu, tüm katmanlar veya düğümleri gösterme, tamamlanmış çıktı Konsolu.](media/uploading-docker-images-complete.png)

<span data-ttu-id="4eb4e-183">**Şekil 4-46**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-183">**Figure 4-46**.</span></span> <span data-ttu-id="4eb4e-184">Düğüm görünümü</span><span class="sxs-lookup"><span data-stu-id="4eb4e-184">View of nodes</span></span>

<span data-ttu-id="4eb4e-185">Sonraki adım, AKS Kubernetes kümenize kapsayıcınızı dağıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="4eb4e-186">Bunun için bir dosyasına ihtiyacınız vardır (**.yml dosyası dağıtma**), aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="4eb4e-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - name: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> <span data-ttu-id="4eb4e-187">Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="4eb4e-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="4eb4e-188">Kullanarak dağıtmak neredeyse hazırsınız artık **Kubectl**, ancak önce bu komutu ile bir AKS kümesi için kimlik bilgilerini edinmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="4eb4e-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Konsolu, yukarıdaki komuttan çıkış: Geçerli bağlamda /root/.kube/config olarak birleştirilmiş "MSSampleK8Cluster](media/getting-aks-credentials.png)

<span data-ttu-id="4eb4e-190">**Şekil 4-47**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-190">**Figure 4-47**.</span></span> <span data-ttu-id="4eb4e-191">kimlik bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="4eb4e-191">getting credentials</span></span>

<span data-ttu-id="4eb4e-192">Ardından, `kubectl create` dağıtımı başlatmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Konsol çıktısı yukarıdaki komutu: dağıtım "oluşturulan mssamplesbook".](media/kubectl-create-command.png)

<span data-ttu-id="4eb4e-195">**Şekil 4-48**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-195">**Figure 4-48**.</span></span> <span data-ttu-id="4eb4e-196">Kubernetes için dağıtma</span><span class="sxs-lookup"><span data-stu-id="4eb4e-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="4eb4e-197">Dağıtım tamamlandığında, bu komutla zamansal olarak erişebileceğiniz bir yerel ara sunucusu ile Kubernetes konsol erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4eb4e-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="4eb4e-198">Ve URL'ye erişilirken `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Kubernetes panosunu, dağıtımlar, pod'ları, çoğaltma kümeleri ve Hizmetleri gösteren tarayıcı görünümü.](media/kubernetes-cluster-information.png)

<span data-ttu-id="4eb4e-200">**Şekil 4-49**.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-200">**Figure 4-49**.</span></span> <span data-ttu-id="4eb4e-201">Kubernetes küme bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4eb4e-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="4eb4e-202">Artık Azure'da bir Linux kapsayıcısı ve Kubernetes AKS kümesi kullanarak, dağıtılan uygulamanız var.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="4eb4e-203">Uygulamanızı Azure portalından alabilirsiniz hizmetinizin genel IP için gözatma erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="4eb4e-204">Bu örnekte bir AKS kümesi oluşturma bölümünde görebilirsiniz [ **Dağıt Azure Kubernetes Service (AKS) için** ](deploy-azure-kubernetes-service.md) üzerinde bu kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="4eb4e-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4eb4e-205">[Önceki](set-up-windows-containers-with-powershell.md)
>[İleri](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="4eb4e-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>

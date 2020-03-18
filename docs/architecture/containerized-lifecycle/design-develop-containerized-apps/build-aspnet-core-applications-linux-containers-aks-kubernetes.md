---
title: Linux konteynerolarak AKS/Kubernetes kümelerine dağıtılan core 2.2 ASP.NET uygulamaları oluşturun
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 02/25/2019
ms.openlocfilehash: ab64a0423ceceb8285c159af276d6d97e12379d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70848747"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="16396-103">Linux konteynerolarak dağıtılan ASP.NET Core 2.2 uygulamalarını AKS/Kubernetes orkestratörüne dönüştürün</span><span class="sxs-lookup"><span data-stu-id="16396-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="16396-104">Azure Kubernetes Services (AKS), Azure'un konteyner dağıtımını ve yönetimini basitleştiren yönetilen Kubernetes orkestrasyon hizmetleridir.</span><span class="sxs-lookup"><span data-stu-id="16396-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="16396-105">AKS'nin başlıca özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="16396-105">AKS main features are:</span></span>

- <span data-ttu-id="16396-106">Azure tarafından barındırılan bir denetim düzlemi</span><span class="sxs-lookup"><span data-stu-id="16396-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="16396-107">Otomatik yükseltmeler</span><span class="sxs-lookup"><span data-stu-id="16396-107">Automated upgrades</span></span>
- <span data-ttu-id="16396-108">Kendi kendini iyileştirme</span><span class="sxs-lookup"><span data-stu-id="16396-108">Self-healing</span></span>
- <span data-ttu-id="16396-109">Kullanıcı yapılandırılabilir ölçekleme</span><span class="sxs-lookup"><span data-stu-id="16396-109">User configurable scaling</span></span>
- <span data-ttu-id="16396-110">Hem geliştiriciler hem de küme işleçleri için daha basit bir kullanıcı deneyimi.</span><span class="sxs-lookup"><span data-stu-id="16396-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="16396-111">Aşağıdaki örnekler, Linux üzerinde çalışan ve Azure'da bir AKS Cluster'a dağıtılan bir ASP.NET Core 2.2 uygulamasının oluşturulmasını incelerken, geliştirme Visual Studio 2017 kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="16396-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="16396-112">Visual Studio 2017'yi kullanarak ASP.NET Core 2.2 Projesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="16396-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="16396-113">ASP.NET Core, Microsoft ve GitHub'daki .NET topluluğu tarafından korunan genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="16396-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="16396-114">Windows, macOS ve Linux'u destekleyen çapraz platformdur ve aygıt, bulut ve gömülü/IoT senaryolarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="16396-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="16396-115">Bu örnek, Visual Studio Web API şablonuna dayanan basit bir proje kullanır, böylece örneği oluşturmak için ek bilgiye ihtiyacınız olmaz.</span><span class="sxs-lookup"><span data-stu-id="16396-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="16396-116">Yalnızca, Core 2.2 teknolojisini kullanarak REST API'li küçük bir projeyi çalıştırmak için tüm öğeleri içeren standart bir şablon kullanarak proje ASP.NETyi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="16396-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Visual Studio'da core web uygulamasını ASP.NET seçerek yeni proje penceresi ekleyin.](media/create-aspnet-core-application.png)

<span data-ttu-id="16396-118">**Şekil 4-36**.</span><span class="sxs-lookup"><span data-stu-id="16396-118">**Figure 4-36**.</span></span> <span data-ttu-id="16396-119">ASP.NET Çekirdek Uygulama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="16396-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="16396-120">Visual Studio'da örnek proje oluşturmak **için, Dosya** > **Yeni** > **Proje'yi**seçin, sol bölmedeki **Web** proje türlerini seçin ve ardından ASP.NET Çekirdek **Web Uygulaması.**</span><span class="sxs-lookup"><span data-stu-id="16396-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="16396-121">Visual Studio, web projeleri için şablonları listeler.</span><span class="sxs-lookup"><span data-stu-id="16396-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="16396-122">Örneğin, ASP.NET bir Web API Uygulaması oluşturmak için **API'yi** seçin.</span><span class="sxs-lookup"><span data-stu-id="16396-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="16396-123">Çerçeve olarak Core 2.2ASP.NET seçtiğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="16396-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="16396-124">.NET Core 2.2, Visual Studio 2017'nin son sürümüne dahildir ve Visual Studio 2017'yi yüklediğinizde otomatik olarak yüklenir ve sizin için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="16396-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![API seçeneği seçili bir ASP.NET Çekirdek Web Uygulaması türünü seçmek için Visual Studio iletişim kutusu.](media/create-web-api-application.png)

<span data-ttu-id="16396-126">**Şekil 4-37.**</span><span class="sxs-lookup"><span data-stu-id="16396-126">**Figure 4-37**.</span></span> <span data-ttu-id="16396-127">CORE 2.2 ve Web API proje türü ASP.NET seçme</span><span class="sxs-lookup"><span data-stu-id="16396-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="16396-128">.NET Core'un önceki bir sürümünüz varsa, 2.2 sürümünü <https://dotnet.microsoft.com/download>'den indirebilir ve yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16396-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="16396-129">Projeyi oluştururken veya sonrasında Docker desteği ekleyebilirsiniz, böylece projenizi istediğiniz zaman "Dockerize" edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16396-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="16396-130">Proje oluşturulduktan sonra Docker desteği eklemek için Solution Explorer'daki proje düğümüne sağ tıklayın ve bağlam menüsünde**Docker ekle desteğini** seçin. **Add** > </span><span class="sxs-lookup"><span data-stu-id="16396-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Varolan bir projeye Docker desteği eklemek için bağlam menüsü seçeneği: Sağ tıklayın (projeye) > > Docker Desteği ekleyin.](media/add-docker-support-to-project.png)

<span data-ttu-id="16396-132">**Şekil 4-38**.</span><span class="sxs-lookup"><span data-stu-id="16396-132">**Figure 4-38**.</span></span> <span data-ttu-id="16396-133">Mevcut projeye Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="16396-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="16396-134">Docker desteğini eklemeyi tamamlamak için Windows veya Linux'u seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16396-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="16396-135">Bu durumda, AKS Windows Kapsayıcılarını desteklemediği için (2018 sonu itibariyle) **Linux'u**seçin.</span><span class="sxs-lookup"><span data-stu-id="16396-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Dockerfile için Hedef İşletim Sistemi'ni seçmek için seçenek iletişim kutusu.](media/select-linux-docker-support.png)

<span data-ttu-id="16396-137">**Şekil 4-39**.</span><span class="sxs-lookup"><span data-stu-id="16396-137">**Figure 4-39**.</span></span> <span data-ttu-id="16396-138">Linux kapsayıcıları seçme.</span><span class="sxs-lookup"><span data-stu-id="16396-138">Selecting Linux containers.</span></span>

<span data-ttu-id="16396-139">Bu basit adımlarla, ASP.NET Core 2.2 uygulamanız bir Linux kapsayıcısı üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="16396-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="16396-140">Gördüğünüz gibi Visual Studio 2017 ve Docker arasındaki entegrasyon tamamen geliştiricinin üretkenliğine odaklıdır.</span><span class="sxs-lookup"><span data-stu-id="16396-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="16396-141">Artık **f5** tuşu ile veya **Oynat** düğmesini kullanarak uygulamanızı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16396-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="16396-142">Projeyi çalıştırdıktan sonra, komutu `docker images` kullanarak görüntüleri listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16396-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="16396-143">Visual Studio `mssampleapplication` 2017 ile projemizin otomatik olarak dağıtılmasıyla oluşturulan görüntüyü görmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="16396-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Docker images komutundan konsol çıkışı, bir liste gösterir: Depo, Etiket, Resim Kimliği, Oluşturulan (tarih) ve Boyut.](media/docker-images-command.png)

<span data-ttu-id="16396-145">**Şekil 4-40.**</span><span class="sxs-lookup"><span data-stu-id="16396-145">**Figure 4-40**.</span></span> <span data-ttu-id="16396-146">Docker görüntülerini görüntüle</span><span class="sxs-lookup"><span data-stu-id="16396-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="16396-147">Çözümü Azure Konteyner Kayıt Defterine Kaydedin</span><span class="sxs-lookup"><span data-stu-id="16396-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="16396-148">Görüntülerin söz kayıt defterinden AKS kümesine dağıtılaabilmesi için resmi [Azure Konteyner Kayıt Defteri (ACR)](https://azure.microsoft.com/services/container-registry/) veya Docker Hub gibi herhangi bir Docker kayıt defterine yükleyin.</span><span class="sxs-lookup"><span data-stu-id="16396-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="16396-149">Bu durumda, resmi Azure Kapsayıcı Kayıt Defteri'ne yüklüyoruz.</span><span class="sxs-lookup"><span data-stu-id="16396-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="16396-150">Görüntüyü Yayın modunda oluşturma</span><span class="sxs-lookup"><span data-stu-id="16396-150">Create the image in Release mode</span></span>

<span data-ttu-id="16396-151">Şimdi, Şekil 4-41'de gösterildiği gibi **Release** **Release**(üretime hazır) görüntü oluşturacağız ve uygulamayı daha önce yaptığımız gibi çalıştıracağız.</span><span class="sxs-lookup"><span data-stu-id="16396-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Sürüm modunda oluşturmak için VS araç çubuğu seçeneği.](media/select-release-mode.png)

<span data-ttu-id="16396-153">**Şekil 4-41.**</span><span class="sxs-lookup"><span data-stu-id="16396-153">**Figure 4-41**.</span></span> <span data-ttu-id="16396-154">Serbest Bırakma Modu'nu Seçme</span><span class="sxs-lookup"><span data-stu-id="16396-154">Selecting Release Mode</span></span>

<span data-ttu-id="16396-155">Komutu `docker image` çalıştırırsanız, biri için diğeri mod `debug` için `release` olmak üzere her iki görüntünün oluşturulduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="16396-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="16396-156">Resim için yeni bir Etiket Oluşturma</span><span class="sxs-lookup"><span data-stu-id="16396-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="16396-157">Her kapsayıcı görüntüsünün kayıt `loginServer` defterinin adıyla etiketlenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="16396-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="16396-158">Bu etiket, görüntü kayıt defterine kapsayıcı görüntüleri gönderilirken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16396-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="16396-159">Azure Konteyner `loginServer` Kayıt Defteri'nden bilgileri alarak adı Azure portalından görüntüleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="16396-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Sağ üstteki Azure kapsayıcı kayıt defteri adının tarayıcı görünümü.](media/loginServer-name.png)

<span data-ttu-id="16396-161">**Şekil 4-42**.</span><span class="sxs-lookup"><span data-stu-id="16396-161">**Figure 4-42**.</span></span> <span data-ttu-id="16396-162">Kayıt Defterinin adının görünümü</span><span class="sxs-lookup"><span data-stu-id="16396-162">View of the name of the Registry</span></span>

<span data-ttu-id="16396-163">Veya aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="16396-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan konsol çıkışı.](media/az-cli-loginServer-name.png)

<span data-ttu-id="16396-165">**Şekil 4-43**.</span><span class="sxs-lookup"><span data-stu-id="16396-165">**Figure 4-43**.</span></span> <span data-ttu-id="16396-166">PowerShell'i kullanarak kayıt defterinin adını alın</span><span class="sxs-lookup"><span data-stu-id="16396-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="16396-167">Her iki durumda da, adı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="16396-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="16396-168">Bizim örneğimizde, `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="16396-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="16396-169">Şimdi en son görüntüyü (Yayın görüntüsü) komutuyla alarak görüntüyü etiketleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="16396-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="16396-170">Komutu `docker tag` çalıştırdıktan sonra, görüntüleri `docker images` komutla listeleyin ve yeni etiketle görüntüyü görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="16396-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Docker images komutundan konsol çıkışı.](media/tagged-docker-images-list.png)

<span data-ttu-id="16396-172">**Şekil 4-44.**</span><span class="sxs-lookup"><span data-stu-id="16396-172">**Figure 4-44**.</span></span> <span data-ttu-id="16396-173">Etiketli resimlerin görünümü</span><span class="sxs-lookup"><span data-stu-id="16396-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="16396-174">Görüntüyü Azure ACR'ye itin</span><span class="sxs-lookup"><span data-stu-id="16396-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="16396-175">Azure Konteyner Kayıt Defteri'nde oturum açın</span><span class="sxs-lookup"><span data-stu-id="16396-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="16396-176">Aşağıdaki komutu kullanarak görüntüyü Azure ACR'ye itin:</span><span class="sxs-lookup"><span data-stu-id="16396-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="16396-177">Bu komut görüntüleri yüklemek biraz zaman alır, ancak işlem sırasında geribildirim verir.</span><span class="sxs-lookup"><span data-stu-id="16396-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Docker push komutundan konsol çıkışı: her katman için karakter tabanlı bir ilerleme çubuğu gösterir.](media/uploading-image-to-acr.png)

<span data-ttu-id="16396-179">**Şekil 4-45.**</span><span class="sxs-lookup"><span data-stu-id="16396-179">**Figure 4-45**.</span></span> <span data-ttu-id="16396-180">Görüntüyü ACR'ye yükleme</span><span class="sxs-lookup"><span data-stu-id="16396-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="16396-181">İşlem tamamlandığında elde ediletmeniz gereken sonucu aşağıda görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="16396-181">You can see below the result you should get when the process completes:</span></span>

![Docker push komutundan konsol çıkışı, tüm katmanları veya düğümleri gösteren tamamlandı.](media/uploading-docker-images-complete.png)

<span data-ttu-id="16396-183">**Şekil 4-46.**</span><span class="sxs-lookup"><span data-stu-id="16396-183">**Figure 4-46**.</span></span> <span data-ttu-id="16396-184">Düğümlerin görünümü</span><span class="sxs-lookup"><span data-stu-id="16396-184">View of nodes</span></span>

<span data-ttu-id="16396-185">Bir sonraki adım, kapsayıcınızı AKS Kubernetes kümenize dağıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="16396-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="16396-186">Bunun için aşağıdakileri içeren bir dosyaya **(.yml dağıtım dosyası)** ihtiyacınız vardır:</span><span class="sxs-lookup"><span data-stu-id="16396-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
> <span data-ttu-id="16396-187">Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="16396-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="16396-188">Şimdi **kubectl**kullanarak dağıtmak için neredeyse hazırsınız, ama önce bu komutile AKS Cluster kimlik bilgilerini almak gerekir:</span><span class="sxs-lookup"><span data-stu-id="16396-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Yukarıdaki komuttan konsol çıkışı: Birleştirilmiş "MSSampleK8Cluster /root/.kube/config'deki geçerli bağlam olarak](media/getting-aks-credentials.png)

<span data-ttu-id="16396-190">**Şekil 4-47.**</span><span class="sxs-lookup"><span data-stu-id="16396-190">**Figure 4-47**.</span></span> <span data-ttu-id="16396-191">kimlik bilgileri alma</span><span class="sxs-lookup"><span data-stu-id="16396-191">getting credentials</span></span>

<span data-ttu-id="16396-192">Ardından, dağıtımı `kubectl create` başlatmak için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="16396-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Yukarıdaki komuttan konsol çıkışı: dağıtım "mssamplesbook" oluşturuldu.](media/kubectl-create-command.png)

<span data-ttu-id="16396-195">**Şekil 4-48**.</span><span class="sxs-lookup"><span data-stu-id="16396-195">**Figure 4-48**.</span></span> <span data-ttu-id="16396-196">Kubernetes’e dağıtma</span><span class="sxs-lookup"><span data-stu-id="16396-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="16396-197">Dağıtım tamamlandığında, kubernetes konsoluna bu komutla zamansal olarak erişebileceğiniz yerel bir proxy ile erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="16396-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="16396-198">Ve url `http://127.0.0.1:8001`erişim .</span><span class="sxs-lookup"><span data-stu-id="16396-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Dağıtımları, Bölmeleri, Çoğaltma Kümelerini ve Hizmetleri gösteren Kubernetes panosunun tarayıcı görünümü.](media/kubernetes-cluster-information.png)

<span data-ttu-id="16396-200">**Şekil 4-49**.</span><span class="sxs-lookup"><span data-stu-id="16396-200">**Figure 4-49**.</span></span> <span data-ttu-id="16396-201">Kubernetes küme bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="16396-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="16396-202">Artık uygulamanızı Bir Linux Kapsayıcısı ve bir AKS Kubernetes Kümesi kullanarak Azure'da dağıttınız.</span><span class="sxs-lookup"><span data-stu-id="16396-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="16396-203">Azure portalından alabileceğiniz uygulamanızın genel IP'sine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16396-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="16396-204">Bu kılavuzda [**Azure Kubernetes Hizmetine (AKS) dağıt**](deploy-azure-kubernetes-service.md) bölümünde bu örnek için AKS Kümesi'nin nasıl oluşturulabileceğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16396-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="16396-205">[Önceki](set-up-windows-containers-with-powershell.md)
>[Sonraki](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="16396-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>

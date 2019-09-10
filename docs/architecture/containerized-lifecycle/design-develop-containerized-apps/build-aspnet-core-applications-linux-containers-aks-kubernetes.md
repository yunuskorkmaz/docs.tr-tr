---
title: AKS/Kubernetes kümelerine Linux kapsayıcıları olarak dağıtılan derleme ASP.NET Core 2,2 uygulamaları
description: Microsoft Platformu ve Araçları ile Kapsayıcı Docker Uygulaması Yaşam Döngüsü
ms.date: 02/25/2019
ms.openlocfilehash: ab64a0423ceceb8285c159af276d6d97e12379d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848747"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="e3dd6-103">AKS/Kubernetes Orchestrator 'a Linux kapsayıcıları olarak dağıtılan derleme ASP.NET Core 2,2 uygulamaları</span><span class="sxs-lookup"><span data-stu-id="e3dd6-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="e3dd6-104">Azure Kubernetes Hizmetleri (AKS), Azure 'un kapsayıcı dağıtımı ve yönetimini kolaylaştıran yönetilen Kubernetes yönetimi hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="e3dd6-105">AKS ana özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e3dd6-105">AKS main features are:</span></span>

- <span data-ttu-id="e3dd6-106">Azure 'da barındırılan denetim düzlemi</span><span class="sxs-lookup"><span data-stu-id="e3dd6-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="e3dd6-107">Otomatik yükseltmeler</span><span class="sxs-lookup"><span data-stu-id="e3dd6-107">Automated upgrades</span></span>
- <span data-ttu-id="e3dd6-108">Kendi kendini onaran</span><span class="sxs-lookup"><span data-stu-id="e3dd6-108">Self-healing</span></span>
- <span data-ttu-id="e3dd6-109">Kullanıcı tarafından yapılandırılabilir ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="e3dd6-109">User configurable scaling</span></span>
- <span data-ttu-id="e3dd6-110">Hem geliştiriciler hem de küme işleçleri için daha basit bir kullanıcı deneyimi.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="e3dd6-111">Aşağıdaki örneklerde, Linux üzerinde çalışan ve Azure 'daki bir AKS kümesine dağıtan ASP.NET Core 2,2 uygulamasının oluşturulması araştırırken Visual Studio 2017 kullanılarak geliştirme yapılır.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="e3dd6-112">Visual Studio 2017 kullanarak ASP.NET Core 2,2 projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3dd6-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="e3dd6-113">ASP.NET Core, GitHub 'da Microsoft ve .NET Community tarafından tutulan genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="e3dd6-114">Windows, macOS ve Linux 'un desteklenme ve cihaz, bulut ve katıştırılmış/IoT senaryolarında kullanılabilen platformlar arası bir platformdur.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="e3dd6-115">Bu örnek, Visual Studio Web API şablonunu temel alan basit bir proje kullanır, bu nedenle örneği oluşturmak için ek bilgiye ihtiyacınız yoktur.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="e3dd6-116">Projeyi, ASP.NET Core 2,2 teknolojisini kullanarak, REST API küçük bir projeyi çalıştırmak için tüm öğeleri içeren standart bir şablon kullanarak oluşturmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Visual Studio 'da ASP.NET Core Web uygulaması ' nı seçerek yeni proje penceresi ekleyin.](media/create-aspnet-core-application.png)

<span data-ttu-id="e3dd6-118">**Şekil 4-36**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-118">**Figure 4-36**.</span></span> <span data-ttu-id="e3dd6-119">ASP.NET Core uygulaması oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="e3dd6-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="e3dd6-120">Visual Studio 'da örnek proje oluşturmak için **Dosya** > **Yeni** > **Proje**' yi seçin, sol bölmedeki **Web** projesi türlerini ve ardından **ASP.NET Core Web uygulaması**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="e3dd6-121">Visual Studio, Web projeleri için şablonlar listeler.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="e3dd6-122">Örneğimiz için **API** 'yi seçerek bir ASP.NET Web API uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="e3dd6-123">Framework olarak ASP.NET Core 2,2 ' i seçtiğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="e3dd6-124">.NET Core 2,2, Visual Studio 2017 ' nin son sürümüne dahildir ve Visual Studio 2017 ' i yüklediğinizde sizin için otomatik olarak yüklenir ve yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![API seçeneği seçili ASP.NET Core Web uygulaması türünü seçmek için Visual Studio iletişim kutusu.](media/create-web-api-application.png)

<span data-ttu-id="e3dd6-126">**Şekil 4-37**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-126">**Figure 4-37**.</span></span> <span data-ttu-id="e3dd6-127">ASP.NET CORE 2,2 ve Web API proje türünü seçme</span><span class="sxs-lookup"><span data-stu-id="e3dd6-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="e3dd6-128">.NET Core 'un önceki bir sürümüne sahipseniz, 2,2 sürümünü <https://dotnet.microsoft.com/download>indirip yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="e3dd6-129">Projeyi oluştururken Docker desteği ekleyebilirsiniz, böylece projenizi istediğiniz zaman "Dockerize" edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="e3dd6-130">Proje oluşturulduktan sonra Docker desteği eklemek için, Çözüm Gezgini içindeki proje düğümüne sağ tıklayın ve bağlam menüsünde**Docker desteği** **Ekle** > ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Mevcut bir projeye Docker desteği eklemek için bağlam menüsü seçeneği: > > Docker desteği eklemek için (projede) öğesine sağ tıklayın.](media/add-docker-support-to-project.png)

<span data-ttu-id="e3dd6-132">**Şekil 4-38**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-132">**Figure 4-38**.</span></span> <span data-ttu-id="e3dd6-133">Mevcut projeye Docker desteği ekleniyor</span><span class="sxs-lookup"><span data-stu-id="e3dd6-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="e3dd6-134">Docker desteği ekleme işleminin tamamlanabilmesi için Windows veya Linux ' u seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="e3dd6-135">Bu durumda, AKS Windows kapsayıcılarını desteklemediğinden (geç 2018 itibariyle) **Linux**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Dockerfile için hedef işletim sistemini seçmek üzere seçenek iletişim kutusu.](media/select-linux-docker-support.png)

<span data-ttu-id="e3dd6-137">**Şekil 4-39**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-137">**Figure 4-39**.</span></span> <span data-ttu-id="e3dd6-138">Linux kapsayıcıları seçiliyor.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-138">Selecting Linux containers.</span></span>

<span data-ttu-id="e3dd6-139">Bu basit adımlarla bir Linux kapsayıcısında çalışan ASP.NET Core 2,2 uygulamanız vardır.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="e3dd6-140">Gördüğünüz gibi, Visual Studio 2017 ile Docker arasındaki tümleştirme, geliştiricinin verimliliğine tamamen dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="e3dd6-141">Artık uygulamanızı **F5** tuşuyla veya **Play** düğmesini kullanarak çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="e3dd6-142">Projeyi çalıştırdıktan sonra, `docker images` komutunu kullanarak görüntüleri listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="e3dd6-143">Visual Studio 2017 ile `mssampleapplication` projemizin otomatik dağıtımı tarafından oluşturulan görüntüyü görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Docker görüntüleri komutundan konsol çıktısı, şunları içeren bir liste gösterir: Depo, etiket, görüntü KIMLIĞI, oluşturulan (Tarih) ve boyut.](media/docker-images-command.png)

<span data-ttu-id="e3dd6-145">**Şekil 4-40**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-145">**Figure 4-40**.</span></span> <span data-ttu-id="e3dd6-146">Docker görüntülerinin görünümü</span><span class="sxs-lookup"><span data-stu-id="e3dd6-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="e3dd6-147">Çözümü Azure Container Registry kaydetme</span><span class="sxs-lookup"><span data-stu-id="e3dd6-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="e3dd6-148">Görüntüyü, [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) veya Docker Hub gibi herhangi bir Docker kayıt defterine yükleyin, bu nedenle görüntüler bu kayıt defterinden aks kümesine dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="e3dd6-149">Bu durumda, görüntüyü Azure Container Registry karşıya yüklüyoruz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="e3dd6-150">Görüntüyü yayın modunda oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3dd6-150">Create the image in Release mode</span></span>

<span data-ttu-id="e3dd6-151">Şimdi, Şekil 4-41 ' de gösterildiği gibi, **yayın**moduna geçiş yaparak ve uygulamayı daha önce yaptığımız gibi çalıştırırken **yayın** modunda (üretim için hazır) görüntü oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Yayın modunda derleme ' deki araç çubuğu seçeneği.](media/select-release-mode.png)

<span data-ttu-id="e3dd6-153">**Şekil 4-41**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-153">**Figure 4-41**.</span></span> <span data-ttu-id="e3dd6-154">Yayın modunu seçme</span><span class="sxs-lookup"><span data-stu-id="e3dd6-154">Selecting Release Mode</span></span>

<span data-ttu-id="e3dd6-155">Komutu çalıştırırsanız, bir için `debug` ve `release` diğeri modu için oluşturulan her iki görüntüyü görürsünüz. `docker image`</span><span class="sxs-lookup"><span data-stu-id="e3dd6-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="e3dd6-156">Görüntü için yeni bir etiket oluşturun</span><span class="sxs-lookup"><span data-stu-id="e3dd6-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="e3dd6-157">Her kapsayıcı görüntüsünün kayıt defteri `loginServer` adıyla etiketlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="e3dd6-158">Bu etiket, kapsayıcı görüntüleri bir görüntü kayıt defterine gönderilirken yönlendirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="e3dd6-159">Azure Container Registry bilgileri alarak Azure Portal `loginServer` adı görüntüleyebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="e3dd6-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Azure Container kayıt defteri adının sağ üst tarafındaki tarayıcı görünümü.](media/loginServer-name.png)

<span data-ttu-id="e3dd6-161">**Şekil 4-42**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-161">**Figure 4-42**.</span></span> <span data-ttu-id="e3dd6-162">Kayıt defterinin adının görünümü</span><span class="sxs-lookup"><span data-stu-id="e3dd6-162">View of the name of the Registry</span></span>

<span data-ttu-id="e3dd6-163">Ya da aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="e3dd6-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan konsol çıktısı.](media/az-cli-loginServer-name.png)

<span data-ttu-id="e3dd6-165">**Şekil 4-43**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-165">**Figure 4-43**.</span></span> <span data-ttu-id="e3dd6-166">PowerShell kullanarak kayıt defterinin adını alın</span><span class="sxs-lookup"><span data-stu-id="e3dd6-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="e3dd6-167">Her iki durumda da adı elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="e3dd6-168">Örneğimizde, `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="e3dd6-169">Artık, şu komutla birlikte en son görüntüyü (yayın görüntüsü) alarak resmi etiketleyebilir:</span><span class="sxs-lookup"><span data-stu-id="e3dd6-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="e3dd6-170">Komutunu çalıştırdıktan sonra, `docker images` komutuyla görüntüleri listeleyin ve yeni etiketiyle birlikte resmi görmeniz gerekir. `docker tag`</span><span class="sxs-lookup"><span data-stu-id="e3dd6-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Docker görüntüleri komutundan konsol çıktısı.](media/tagged-docker-images-list.png)

<span data-ttu-id="e3dd6-172">**Şekil 4-44**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-172">**Figure 4-44**.</span></span> <span data-ttu-id="e3dd6-173">Etiketli görüntülerin görünümü</span><span class="sxs-lookup"><span data-stu-id="e3dd6-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="e3dd6-174">Görüntüyü Azure ACR 'ye gönderme</span><span class="sxs-lookup"><span data-stu-id="e3dd6-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="e3dd6-175">Azure Container Registry oturum açın</span><span class="sxs-lookup"><span data-stu-id="e3dd6-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="e3dd6-176">Aşağıdaki komutu kullanarak görüntüyü Azure ACR 'ye gönderin:</span><span class="sxs-lookup"><span data-stu-id="e3dd6-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="e3dd6-177">Bu komut, görüntüleri karşıya yüklerken bir işlem gerçekleştirir, ancak işlemde geri bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Docker Push komutundan konsol çıkışı: her katman için bir karakter tabanlı ilerleme çubuğu gösterir.](media/uploading-image-to-acr.png)

<span data-ttu-id="e3dd6-179">**Şekil 4-45**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-179">**Figure 4-45**.</span></span> <span data-ttu-id="e3dd6-180">Görüntüyü ACR 'ye yükleme</span><span class="sxs-lookup"><span data-stu-id="e3dd6-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="e3dd6-181">İşlem tamamlandığında almanız gereken sonucun altına bakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e3dd6-181">You can see below the result you should get when the process completes:</span></span>

![Docker Push komutundan konsol çıktısı, tüm katmanları veya düğümleri gösterir.](media/uploading-docker-images-complete.png)

<span data-ttu-id="e3dd6-183">**Şekil 4-46**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-183">**Figure 4-46**.</span></span> <span data-ttu-id="e3dd6-184">Düğümlerin görünümü</span><span class="sxs-lookup"><span data-stu-id="e3dd6-184">View of nodes</span></span>

<span data-ttu-id="e3dd6-185">Bir sonraki adım, kapsayıcınızı AKS Kubernetes kümenize dağıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="e3dd6-186">Bunun için, aşağıdakileri içeren bir dosya ( **. yml dağıtım dosyası**) gerekir:</span><span class="sxs-lookup"><span data-stu-id="e3dd6-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
> <span data-ttu-id="e3dd6-187">Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="e3dd6-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="e3dd6-188">Artık, **Kubectl**kullanarak dağıtıma hazırsınız, ancak önce bu komutla aks kümesi için kimlik bilgilerini almalısınız:</span><span class="sxs-lookup"><span data-stu-id="e3dd6-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Yukarıdaki komuttan konsol çıkışı: "MSSampleK8Cluster as geçerli Context/root/. Kube/config içinde birleştirildi](media/getting-aks-credentials.png)

<span data-ttu-id="e3dd6-190">**Şekil 4-47**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-190">**Figure 4-47**.</span></span> <span data-ttu-id="e3dd6-191">kimlik bilgileri alınıyor</span><span class="sxs-lookup"><span data-stu-id="e3dd6-191">getting credentials</span></span>

<span data-ttu-id="e3dd6-192">Ardından, dağıtımı başlatmak `kubectl create` için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Yukarıdaki komuttan konsol çıkışı: dağıtım "mssamplesbook" oluşturuldu.](media/kubectl-create-command.png)

<span data-ttu-id="e3dd6-195">**Şekil 4-48**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-195">**Figure 4-48**.</span></span> <span data-ttu-id="e3dd6-196">Kubernetes 'e dağıtma</span><span class="sxs-lookup"><span data-stu-id="e3dd6-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="e3dd6-197">Dağıtım tamamlandığında, bu komutla zamana bağlı erişebileceğiniz bir yerel ara sunucu ile Kubernetes konsoluna erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e3dd6-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="e3dd6-198">Ve URL `http://127.0.0.1:8001`'ye erişme.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Dağıtım, dizin, çoğaltma kümesi ve hizmet gösteren Kubernetes panosunun tarayıcı görünümü.](media/kubernetes-cluster-information.png)

<span data-ttu-id="e3dd6-200">**Şekil 4-49**.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-200">**Figure 4-49**.</span></span> <span data-ttu-id="e3dd6-201">Kubernetes kümesi bilgilerini görüntüle</span><span class="sxs-lookup"><span data-stu-id="e3dd6-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="e3dd6-202">Artık uygulamanız Azure 'da, bir Linux kapsayıcısı ve bir AKS Kubernetes kümesi kullanılarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="e3dd6-203">Uygulamanızın, hizmetinizin genel IP 'ye gözatmasına erişerek Azure portal edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="e3dd6-204">Bu kılavuzda [**Azure Kubernetes Service 'e (aks) dağıtım**](deploy-azure-kubernetes-service.md) bölümünde bu örnek için aks kümesini nasıl oluşturacağınız hakkında bilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3dd6-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e3dd6-205">[Önceki](set-up-windows-containers-with-powershell.md)İleri
>[](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="e3dd6-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>

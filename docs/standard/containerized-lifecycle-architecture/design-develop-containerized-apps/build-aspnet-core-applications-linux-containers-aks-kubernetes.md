---
title: AKS/Kubernetes kümeler halinde Linux kapsayıcıları olarak dağıtılan bir ASP.NET Core 2.1 uygulamaları oluşturun
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: b03b6fab9dcd53e97c2bc4d7e5c958ca4b931077
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221402"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-akskubernetes-orchestrator"></a><span data-ttu-id="6d0a4-103">AKS/Kubernetes orchestrator Linux kapsayıcıları olarak dağıtılan bir ASP.NET Core 2.1 uygulamaları oluşturun</span><span class="sxs-lookup"><span data-stu-id="6d0a4-103">Build ASP.NET Core 2.1 applications deployed as Linux containers into AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="6d0a4-104">Azure Kubernetes Hizmetleri (AKS), kapsayıcı dağıtımı ve Yönetimi basitleştirin Azure'nın yönetilen Kubernetes düzenlemeleri hizmetleridir.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="6d0a4-105">AKS ana özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6d0a4-105">AKS main features are:</span></span>

- <span data-ttu-id="6d0a4-106">Azure'da barındırılan denetim düzlemi</span><span class="sxs-lookup"><span data-stu-id="6d0a4-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="6d0a4-107">Otomatik yükseltme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-107">Automated upgrades</span></span>
- <span data-ttu-id="6d0a4-108">Kendi kendine iyileştirme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-108">Self-healing</span></span>
- <span data-ttu-id="6d0a4-109">Kullanıcı yapılandırılabilir ölçeklendirme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-109">User configurable scaling</span></span>
- <span data-ttu-id="6d0a4-110">Hem geliştiriciler hem de küme operatörleri için basit bir kullanıcı deneyimi.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="6d0a4-111">Aşağıdaki örnekte bir AKS kümesi, azure'da geliştirme yapıldığı sırada dağıtır ve Linux üzerinde çalışan bir ASP.NET Core 2.1 uygulama oluşturulmasını keşfedin Visual Studio 2017'yi kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-111">The following examples explore the creation of an ASP.NET Core 2.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a><span data-ttu-id="6d0a4-112">Visual Studio 2017'yi kullanarak ASP.NET Core 2.1 projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d0a4-112">Creating the ASP.NET Core 2.1 Project using Visual Studio 2017</span></span>

<span data-ttu-id="6d0a4-113">ASP.NET Core, Microsoft ve GitHub üzerinde .NET topluluk tarafından korunan bir genel amaçlı bir geliştirme platformudur.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="6d0a4-114">Bu Windows, macOS ve Linux'ta destekleyen platformlar arası ve cihaz, Bulut ve katıştırılmış IOT senaryoları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-114">It is cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="6d0a4-115">Bu örnek, örnek oluşturmak için ek bilgisine ihtiyacınız yoktur, bir Visual Studio Web API şablonuna dayanan dayalı basit bir projesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-115">This example uses a simple project that's based based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="6d0a4-116">Bir ASP.NET Core 2.1 teknolojisini kullanarak REST API'sini küçük bir proje çalıştırmak için tüm öğeleri içeren bir standart şablonu kullanarak proje oluşturmak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.1 technology.</span></span>

![Yeni Proje penceresinin Visual Studio kullanarak ASP.NET Core Web uygulaması seçme ekleyin.](media/create-aspnet-core-application.png)

<span data-ttu-id="6d0a4-118">**Şekil 4-36**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-118">**Figure 4-36**.</span></span> <span data-ttu-id="6d0a4-119">ASP.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d0a4-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="6d0a4-120">Örnek proje oluşturmak için Seç sahip **dosya** > **yeni** > **proje** Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-120">To create the sample project, you have to select **File** > **New** > **Project** on Visual Studio.</span></span> <span data-ttu-id="6d0a4-121">Aranacak sahip olduğu bir proje, çeşitli türleri için şablonlar listesi görürsünüz sonra **Web** > **.NET Core** Sol paneldeki.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-121">Then you'll see a list of templates for several types of projects, where you have to look for **Web** > **.NET Core** on the left panel.</span></span> <span data-ttu-id="6d0a4-122">Bu örnek için select **ASP.NET Core Web uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-122">For this example select **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="6d0a4-123">Sonraki iletişim kutusunda, .NET Core ve ASP.NET Core 2.1 hedef çerçeve Şekil 4-37 gösterilen üst pulldowns olarak seçtiniz ve ASP.NET Core Web API uygulaması oluşturmak için API seçeneğini seçip emin olun.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-123">In the next dialog ensure that you have selected .NET Core and ASP.NET Core 2.1 as the target framework in the top pulldowns, as shown in figure 4-37, and then select the API option, to create an ASP.NET Core Web API application.</span></span>

<span data-ttu-id="6d0a4-124">.NET Core 2.1 dahil Visual Studio 2017 sürüm 15.7.0 ya da daha büyük ve otomatik olarak yüklenir ve seçtiğiniz sizin için yapılandırılır **.NET Core çoklu platform geliştirme** yüklemesi sırasında iş yükü.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-124">The .NET Core 2.1 is included in Visual Studio 2017 version 15.7.0 or higher and is automatically installed and configured for you when you select the **.NET Core cross-platform development** workload during installation.</span></span>

![API seçeneği belirlenmiş bir ASP.NET Core Web uygulaması türünü seçmek için visual Studio iletişim.](media/create-web-api-application.png)

<span data-ttu-id="6d0a4-126">**Şekil 4-37**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-126">**Figure 4-37**.</span></span> <span data-ttu-id="6d0a4-127">ASP.NET CORE 2.1 seçme ve Web API proje türü</span><span class="sxs-lookup"><span data-stu-id="6d0a4-127">Selecting ASP.NET CORE 2.1 and Web API project type</span></span>

<span data-ttu-id="6d0a4-128">.NET Core herhangi bir önceki sürümü varsa, indirin ve 2.1 sürümü <https://www.microsoft.com/net/download/core#/sdk>.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-128">If you have any previous version of .NET Core, you can download and install the 2.1 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="6d0a4-129">Önceki adımda ya da daha sonra projeyi başlattıktan sonra gerekirse projesi oluşturduğunuz sırada, Docker desteği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-129">You can add Docker support when creating the project in the previous step, or later, if the need arises after starting the project.</span></span> <span data-ttu-id="6d0a4-130">Proje oluşturulduktan sonra Docker desteğini eklemesi için proje dosyasında sağ **Çözüm Gezgini** seçip **Ekle** > **Docker desteği** üzerinde bağlam menüsü.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-130">To add the Docker support after the project creation, right-click on the project file in the **Solution Explorer** and select **Add** > **Docker support** on the context menu.</span></span>

![Mevcut bir projeye Docker desteği eklemek için bağlam menüsü seçeneği: (Proje) sağ tıklayın > Ekle > Docker desteği.](media/add-docker-support-to-project.png)

<span data-ttu-id="6d0a4-132">**Şekil 4-38**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-132">**Figure 4-38**.</span></span> <span data-ttu-id="6d0a4-133">Var olan bir projeye Docker desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="6d0a4-134">Docker destek eklemeyi tamamlamak için Windows veya Linux seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-134">To complete adding Docker support, you have the choice of Windows or Linux.</span></span> <span data-ttu-id="6d0a4-135">Bu örnekte **Linux**, çünkü AKS Windows kapsayıcıları (olarak, geç 2018) desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Hedef işletim sistemi için bir Dockerfile seçin iletişim seçeneği.](media/select-linux-docker-support.png)

<span data-ttu-id="6d0a4-137">**Şekil 4-39**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-137">**Figure 4-39**.</span></span> <span data-ttu-id="6d0a4-138">Linux kapsayıcıları seçme.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-138">Selecting Linux containers.</span></span>

<span data-ttu-id="6d0a4-139">Bu basit adımları uygulayarak bir Linux kapsayıcısı üzerinde çalışan ASP.NET Core 2.1 uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-139">With these simple steps, you will have your ASP.NET Core 2.1 application running on a Linux container.</span></span>

<span data-ttu-id="6d0a4-140">Gördüğünüz gibi Visual Studio 2017 ile Docker arasında tümleştirme için geliştirici üretkenliği tamamen yönlendirilmiş demektir.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="6d0a4-141">Basabilirsiniz artık **F5** oluşturup çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-141">Now you can press **F5** to build and run your application.</span></span>

<span data-ttu-id="6d0a4-142">Proje çalıştırdıktan sonra kullanarak görüntüleri listeleyebilirsiniz `docker images` komutu.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="6d0a4-143">Görmelisiniz `mssampleapplication` otomatik dağıtma, projenin Visual Studio 2017 ile oluşturulan görüntü.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-143">You should see the `mssampleapplication` image created with the automatic deploy of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Konsol docker görüntüleri komuttan çıkış ile gösterilir: Depo, etiket, görüntü kimliği, oluşturulan (tarih) ve boyutu.](media/docker-images-command.png)

<span data-ttu-id="6d0a4-145">**Şekil 4-40**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-145">**Figure 4-40**.</span></span> <span data-ttu-id="6d0a4-146">Docker görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="6d0a4-147">Azure kapsayıcı kayıt defterinde çözümü</span><span class="sxs-lookup"><span data-stu-id="6d0a4-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="6d0a4-148">Resim gibi herhangi bir Docker kayıt defterine yükleyin [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) veya Docker hub'ı AKS kümeye, kayıt defterinden görüntüleri dağıtılacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="6d0a4-149">Bu durumda, biz görüntü Azure Container Registry'ye yükleme.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="6d0a4-150">Yayın modunda görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d0a4-150">Create the image in Release mode</span></span>

<span data-ttu-id="6d0a4-151">Görüntüyü oluşturmak **yayın** burada gösterildiği gibi sürümüne (üretim için hazır) modunu değiştirme ve uygulamayı yeniden çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-151">Create the image in **Release** Mode (ready for production) changing to Release as shown here and press F5 to run the application again.</span></span>

![Yayın modunda oluşturmak için VS araç seçeneği.](media/select-release-mode.png)

<span data-ttu-id="6d0a4-153">**Şekil 4-41**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-153">**Figure 4-41**.</span></span> <span data-ttu-id="6d0a4-154">Sürüm modu seçme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-154">Selecting Release Mode</span></span>

<span data-ttu-id="6d0a4-155">Yürütüyorsa `docker image` komutu, oluşturulan her iki görüntüleri göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-155">If you execute the `docker image` command, you'll see both images created.</span></span> <span data-ttu-id="6d0a4-156">Birincisi `debug` diğeri `release` modu.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-156">One for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="6d0a4-157">Yeni bir etiket oluşturmak için görüntü</span><span class="sxs-lookup"><span data-stu-id="6d0a4-157">Create a new Tag for the Image</span></span>

<span data-ttu-id="6d0a4-158">Her kapsayıcı görüntüsü ile etiketlenmesi gerekir `loginServer` kayıt defteri adı.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-158">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="6d0a4-159">Bu etiket, görüntü kayıt defterine kapsayıcı görüntüleri gönderirken yönlendirme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-159">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="6d0a4-160">Görüntüleyebileceğiniz `loginServer` ad Azure portalı, Azure Container Registry'den bilgileri alma</span><span class="sxs-lookup"><span data-stu-id="6d0a4-160">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Sağ üst kısımdaki tarayıcı görünümü, Azure kapsayıcı kayıt defteri adı.](media/loginServer-name.png)

<span data-ttu-id="6d0a4-162">**Şekil 4-42**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-162">**Figure 4-42**.</span></span> <span data-ttu-id="6d0a4-163">Kayıt defteri adını görüntüle</span><span class="sxs-lookup"><span data-stu-id="6d0a4-163">View of the name of the Registry</span></span>

<span data-ttu-id="6d0a4-164">Veya aşağıdaki komutu çalıştırarak:</span><span class="sxs-lookup"><span data-stu-id="6d0a4-164">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Yukarıdaki komuttan çıkış konsol.](media/az-cli-loginServer-name.png)

<span data-ttu-id="6d0a4-166">**Şekil 4-43**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-166">**Figure 4-43**.</span></span> <span data-ttu-id="6d0a4-167">PowerShell kullanarak kayıt defteri adını alın</span><span class="sxs-lookup"><span data-stu-id="6d0a4-167">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="6d0a4-168">Her iki durumda da adı elde.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-168">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="6d0a4-169">Bizim örneğimizde `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-169">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="6d0a4-170">Artık son görüntü (sürüm görüntü) aşağıdaki komutla alma görüntü etiketleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d0a4-170">Now you can tag the image, taking the latest image (Release image), with the following command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="6d0a4-171">Çalıştırdıktan sonra `docker tag` komutu, görüntülerle listesi `docker images` komutu.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-171">After running the `docker tag` command, list the images with the `docker images` command.</span></span> <span data-ttu-id="6d0a4-172">Yeni etiket görüntüsüyle görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-172">You should see the image with the new tag.</span></span>

![Docker görüntüleri komuttan çıkış konsol.](media/tagged-docker-images-list.png)

<span data-ttu-id="6d0a4-174">**Şekil 4-44**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-174">**Figure 4-44**.</span></span> <span data-ttu-id="6d0a4-175">Etiketli Görüntü görüntüle</span><span class="sxs-lookup"><span data-stu-id="6d0a4-175">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="6d0a4-176">Azure ACR görüntü gönderme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-176">Push the image into the Azure ACR</span></span>

<span data-ttu-id="6d0a4-177">Aşağıdaki komutu kullanarak Azure ACR görüntüyü gönderin:</span><span class="sxs-lookup"><span data-stu-id="6d0a4-177">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="6d0a4-178">Bu komut biraz uzun sürebilir. görüntü karşıya ancak işlem sırasında geri bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-178">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Konsol çıktısı docker itme komutundan: her katman için bir karakter tabanlı bir ilerleme çubuğu gösterir.](media/uploading-image-to-acr.png)

<span data-ttu-id="6d0a4-180">**Şekil 4-45**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-180">**Figure 4-45**.</span></span> <span data-ttu-id="6d0a4-181">Görüntüyü ACR'ye yükleme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-181">Uploading the image to the ACR</span></span>

<span data-ttu-id="6d0a4-182">İşlem tamamlandığında almalısınız sonucu görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d0a4-182">You can see below the result you should get when the process completes:</span></span>

![Docker push komutu, tüm katmanlar veya düğümleri gösterme, tamamlanmış çıktı Konsolu.](media/uploading-docker-images-complete.png)

<span data-ttu-id="6d0a4-184">**Şekil 4-46**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-184">**Figure 4-46**.</span></span> <span data-ttu-id="6d0a4-185">Düğüm görünümü</span><span class="sxs-lookup"><span data-stu-id="6d0a4-185">View of nodes</span></span>

<span data-ttu-id="6d0a4-186">Sonraki adım, AKS Kubernetes kümenize kapsayıcınızı dağıtmaktır.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-186">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="6d0a4-187">Bunun için bir dosya gereksinim (**.yml dosyası dağıtma**), bu durumda, içerir:</span><span class="sxs-lookup"><span data-stu-id="6d0a4-187">For that you need a file (**.yml deploy file**) that, in this case, contains:</span></span>

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
        - mane: mssample-services-app
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
> <span data-ttu-id="6d0a4-188">Kubernetes ile dağıtım hakkında daha fazla bilgi için bkz: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="6d0a4-188">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="6d0a4-189">Kullanarak dağıtmak neredeyse hazırsınız artık **Kubectl**, ancak önce bu komutu ile bir AKS kümesi için kimlik bilgilerini edinmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="6d0a4-189">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Konsolu, yukarıdaki komuttan çıkış: Geçerli bağlamda /root/.kube/config olarak birleştirilmiş "MSSampleK8Cluster](media/getting-aks-credentials.png)

<span data-ttu-id="6d0a4-191">**Şekil 4-47**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-191">**Figure 4-47**.</span></span> <span data-ttu-id="6d0a4-192">kimlik bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="6d0a4-192">getting credentials</span></span>

<span data-ttu-id="6d0a4-193">Ardından, `kubectl create` dağıtımı başlatmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-193">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Konsol çıktısı yukarıdaki komutu: dağıtım "oluşturulan mssamplesbook".](media/kubectl-create-command.png)

<span data-ttu-id="6d0a4-196">**Şekil 4-48**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-196">**Figure 4-48**.</span></span> <span data-ttu-id="6d0a4-197">Kubernetes için dağıtma</span><span class="sxs-lookup"><span data-stu-id="6d0a4-197">Deploy to Kubernetes</span></span>

<span data-ttu-id="6d0a4-198">Dağıtım tamamlandığında, bu komutla zamansal olarak erişebileceğiniz bir yerel ara sunucusu ile Kubernetes konsol erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6d0a4-198">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="6d0a4-199">Ve URL'ye erişilirken `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-199">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Kubernetes panosunu, dağıtımlar, pod'ları, çoğaltma kümeleri ve Hizmetleri gösteren tarayıcı görünümü.](media/kubernetes-cluster-information.png)

<span data-ttu-id="6d0a4-201">**Şekil 4-49**.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-201">**Figure 4-49**.</span></span> <span data-ttu-id="6d0a4-202">Kubernetes küme bilgilerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6d0a4-202">View Kubernetes cluster information</span></span>

<span data-ttu-id="6d0a4-203">Artık Azure'da bir Linux kapsayıcısı ve Kubernetes AKS kümesi kullanarak, dağıtılan uygulamanız var.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-203">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="6d0a4-204">Uygulamanızı Azure portalından alabilirsiniz hizmetinizin genel IP için gözatma erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-204">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="6d0a4-205">Bu örnekte bir AKS kümesi oluşturma bölümünde görebilirsiniz [ **Dağıt Azure Kubernetes Service (AKS) için** ](deploy-azure-kubernetes-service.md) üzerinde bu kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="6d0a4-205">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6d0a4-206">[Önceki](set-up-windows-containers-with-powershell.md)
>[İleri](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="6d0a4-206">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>

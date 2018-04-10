---
title: Docker çalışan konsol uygulamaları
description: Varolan bir .NET Framework konsol uygulaması almak ve bir Windows Docker kapsayıcısı çalıştırmak öğrenin.
author: spboyer
keywords: .NET, kapsayıcı, konsol, uygulamaları
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 7990ed03028ea9361a8b1760b237b8ed2f9d204d
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="running-console-applications-in-windows-containers"></a><span data-ttu-id="d842b-104">Windows kapsayıcılarında çalışan konsol uygulamaları</span><span class="sxs-lookup"><span data-stu-id="d842b-104">Running console applications in Windows containers</span></span>

<span data-ttu-id="d842b-105">Konsol uygulamaları birçok amaçlar için kullanılır; Basit durum uzun süre çalışan belge görüntüsüne sorgulamasını görevleri işleniyor.</span><span class="sxs-lookup"><span data-stu-id="d842b-105">Console applications are used for many purposes; from simple querying of a status to long running document image processing tasks.</span></span> <span data-ttu-id="d842b-106">Herhangi bir durumda, başlatılması ve bu uygulamaları ölçeklendirme olanağı karşılanmadığı donanım satın almalar, başlatma süreleri veya birden çok örneği çalıştıran kısıtlamalarla.</span><span class="sxs-lookup"><span data-stu-id="d842b-106">In any case, the ability to start up and scale these applications are met with limitations of hardware acquisitions, startup times or running multiple instances.</span></span>

<span data-ttu-id="d842b-107">Docker ve Windows Server kullanmak için konsol uygulamaları taşıma kapsayıcıları sağlar işlem ve ardından kapatma düzgün bir şekilde gerçekleştirmek üzere bunları etkinleştirme temiz bir durumdan bu uygulamaları başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="d842b-107">Moving your console applications to use Docker and Windows Server containers allows for starting these applications from a clean state, enabling them to perform the operation and then shutdown cleanly.</span></span> <span data-ttu-id="d842b-108">Bu konuda, bir Windows konsol uygulaması taşımak için gerekli olan adımları kapsayıcı temel ve bunu bir PowerShell Betiği kullanılarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="d842b-108">This topic will show the steps needed to move a console application to a Windows based container and start it using a PowerShell script.</span></span>

<span data-ttu-id="d842b-109">Örnek konsol uygulaması bağımsız değişken, bir soru bu durumda alır ve rastgele bir yanıt döndüren basit bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="d842b-109">The sample console application is a simple example which takes an argument, a question in this case, and returns a random answer.</span></span> <span data-ttu-id="d842b-110">Bu sürebilir bir `customer_id` ve bunların vergileri işlem veya için bir küçük resim oluşturma bir `image_url` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d842b-110">This could take a `customer_id` and process their taxes, or create a thumbnail for an `image_url` argument.</span></span>

<span data-ttu-id="d842b-111">Yanıt yanı sıra `Environment.MachineName` uygulama yerel olarak ve bir Windows kapsayıcıda çalışan arasındaki farkı göstermek için yanıta eklenir.</span><span class="sxs-lookup"><span data-stu-id="d842b-111">In addition to the answer, the `Environment.MachineName` has been added to the response to show the difference between running the application locally and in a Windows container.</span></span> <span data-ttu-id="d842b-112">Uygulamayı yerel olarak çalışırken, yerel makine adınızı döndürülmelidir ve bir Windows kapsayıcısında; çalıştırırken kapsayıcı oturum kimliği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="d842b-112">When running the application locally, your local machine name should be returned and when running in a Windows Container; the container session id is returned.</span></span>

<span data-ttu-id="d842b-113">[Tam örnek](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) github'da dotnet/samples Havuzda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d842b-113">The [complete example](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) is available in the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="d842b-114">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d842b-114">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="d842b-115">Bir kapsayıcı uygulamanıza taşıma çalışmaya başlamadan önce koşulları bazı Docker ile ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d842b-115">You need to be familiar with some Docker terms before you begin working on moving your application to a container.</span></span>

> <span data-ttu-id="d842b-116">A *Docker görüntü* ortam için işletim sistemi (OS), sistem bileşenleri ve uygulamaları dahil olmak üzere, çalışan bir kapsayıcı tanımlar salt okunur bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="d842b-116">A *Docker image* is a read-only template that defines the environment for a running container, including the operating system (OS), system components, and application(s).</span></span>

<span data-ttu-id="d842b-117">Görüntüleri temel bir görüntüden oluşan Docker görüntülerinin bir önemli özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="d842b-117">One important feature of Docker images is that images are composed from a base image.</span></span> <span data-ttu-id="d842b-118">Her yeni görüntüyü küçük bir özellikler kümesi için varolan bir görüntü ekler.</span><span class="sxs-lookup"><span data-stu-id="d842b-118">Each new image adds a small set of features to an existing image.</span></span> 

> <span data-ttu-id="d842b-119">A *Docker kapsayıcısı* bir görüntü, çalışan bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="d842b-119">A *Docker container* is a running instance of an image.</span></span> 

<span data-ttu-id="d842b-120">Aynı görüntüyü birçok kapsayıcılarında çalıştırarak uygulama ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="d842b-120">You scale an application by running the same image in many containers.</span></span>
<span data-ttu-id="d842b-121">Kavramsal olarak, bu aynı uygulamayı birden çok ana çalıştırmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="d842b-121">Conceptually, this is similar to running the same application in multiple hosts.</span></span>

<span data-ttu-id="d842b-122">Docker mimarisi hakkında daha fazla okuyarak bilgi [Docker genel bakış](https://docs.docker.com/engine/understanding-docker/) Docker sitesinde.</span><span class="sxs-lookup"><span data-stu-id="d842b-122">You can learn more about the Docker architecture by reading the [Docker Overview](https://docs.docker.com/engine/understanding-docker/) on the Docker site.</span></span> 

<span data-ttu-id="d842b-123">Konsol uygulamanızın taşıma birkaç adım bir konudur.</span><span class="sxs-lookup"><span data-stu-id="d842b-123">Moving your console application is a matter of a few steps.</span></span>

1. [<span data-ttu-id="d842b-124">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="d842b-124">Build the application</span></span>](#building-the-application)
1. [<span data-ttu-id="d842b-125">Görüntüsü için bir Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d842b-125">Creating a Dockerfile for the image</span></span>](#creating-the-dockerfile)
1. [<span data-ttu-id="d842b-126">Derleme ve Docker kapsayıcısı çalıştırma işlemi</span><span class="sxs-lookup"><span data-stu-id="d842b-126">Process to build and run the Docker container</span></span>](#creating-the-image)

## <a name="prerequisites"></a><span data-ttu-id="d842b-127">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d842b-127">Prerequisites</span></span>
<span data-ttu-id="d842b-128">Windows kapsayıcıları üzerinde desteklenir [Windows 10 Anniversary güncelleştirme](https://www.microsoft.com/en-us/software-download/windows10/) veya [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span><span class="sxs-lookup"><span data-stu-id="d842b-128">Windows containers are supported on [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) or [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span></span>

> [!NOTE]
><span data-ttu-id="d842b-129">Windows Server 2016 kullanıyorsanız, Docker için Windows Installer özelliğini etkinleştirmemeniz beri kapsayıcıları el ile etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d842b-129">If you are using Windows Server 2016, you must enable containers manually since the Docker for Windows installer will not enable the feature.</span></span> <span data-ttu-id="d842b-130">Tüm güncelleştirmeler için işletim sistemi çalıştıran ve makalesindeki yönergeleri izleyin emin olun [kapsayıcı konak dağıtımı](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) kapsayıcıları ve Docker özellikleri yüklemek için makale.</span><span class="sxs-lookup"><span data-stu-id="d842b-130">Make sure all updates have run for the OS and then follow the instructions from the [Container Host Deployment](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) article to install the containers and Docker features.</span></span>

<span data-ttu-id="d842b-131">Docker için Windows, sürüm 1.12 desteklemek için Beta 26 ya da daha yüksek Windows kapsayıcıları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d842b-131">You need to have Docker for Windows, version 1.12 Beta 26 or higher to support Windows containers.</span></span> <span data-ttu-id="d842b-132">Varsayılan olarak, Linux tabanlı kapsayıcıları Docker sağlar; geçiş Windows kapsayıcılara sistem tepsisindeki Docker simgesini sağ tıklayarak ve seçin **geçiş Windows kapsayıcılara**.</span><span class="sxs-lookup"><span data-stu-id="d842b-132">By default, Docker enables Linux based containers; switch to Windows containers by right clicking the Docker icon in the system tray and select **Switch to Windows containers**.</span></span> <span data-ttu-id="d842b-133">Docker değiştirme işlemi çalışacak ve yeniden başlatma gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="d842b-133">Docker will run the process to change and a restart may be required.</span></span>

![Windows kapsayıcıları](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a><span data-ttu-id="d842b-135">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="d842b-135">Building the application</span></span>
<span data-ttu-id="d842b-136">Yükleyici, FTP veya dosya paylaşımı konsol uygulamaları genellikle dağıtılmış dağıtım.</span><span class="sxs-lookup"><span data-stu-id="d842b-136">Typically console applications are distributed through an installer, FTP, or File Share deployment.</span></span> <span data-ttu-id="d842b-137">Bir kapsayıcıya dağıtırken varlıklar derlenir ve Docker görüntü oluşturulduğunda, kullanılabilir bir konuma hazırlanan gerekir.</span><span class="sxs-lookup"><span data-stu-id="d842b-137">When deploying to a container, the assets need to be compiled and staged to a location that can be used when the Docker image is created.</span></span>

<span data-ttu-id="d842b-138">İçinde *build.ps1*, komut dosyası kullanan [MSBuild](/visualstudio/msbuild/msbuild) varlıkları oluşturma görevini tamamlamak için uygulamayı derlemek için.</span><span class="sxs-lookup"><span data-stu-id="d842b-138">In *build.ps1*, the script uses [MSBuild](/visualstudio/msbuild/msbuild) to compile the application to complete the task of building the assets.</span></span> <span data-ttu-id="d842b-139">Gerekli varlıklar sonlandırmaya MSBuild için geçirilen birkaç parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="d842b-139">There are a few parameters passed to MSBuild to finalize the needed assets.</span></span> <span data-ttu-id="d842b-140">Proje dosyası veya derlenecek çözüm, konum adı çıkış ve son olarak yapılandırma (sürüm ya da hata ayıklama).</span><span class="sxs-lookup"><span data-stu-id="d842b-140">The name of the project file or solution to be compiled, the location for the output and finally the configuration (Release or Debug).</span></span>

<span data-ttu-id="d842b-141">Çağrısında `Invoke-MSBuild` `OutputPath` ayarlanır **yayımlama** ve `Configuration` kümesine **sürüm**.</span><span class="sxs-lookup"><span data-stu-id="d842b-141">In the call to `Invoke-MSBuild` the `OutputPath` is set to **publish** and  `Configuration` set to **Release**.</span></span> 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a><span data-ttu-id="d842b-142">Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="d842b-142">Creating the Dockerfile</span></span>
<span data-ttu-id="d842b-143">.NET Framework uygulama Konsolu için kullanılan temel görüntü `microsoft/windowsservercore`, genel kullanıma açık üzerinde [Docker hub'a](https://hub.docker.com/r/microsoft/windowsservercore/).</span><span class="sxs-lookup"><span data-stu-id="d842b-143">The base image used for a console .NET Framework application is `microsoft/windowsservercore`, publicly available on [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span></span> <span data-ttu-id="d842b-144">Temel görüntü en az bir Windows Server 2016, .NET Framework 4.6.2 yüklemesini içerir ve Windows kapsayıcıları için temel işletim sistemi görüntüsü görev yapar.</span><span class="sxs-lookup"><span data-stu-id="d842b-144">The base image contains a minimal installation of Windows Server 2016, .NET Framework 4.6.2 and serves as the base OS image for Windows Containers.</span></span>

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
<span data-ttu-id="d842b-145">Temel görüntü kullanarak Dockerfile ilk satırı atar [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="d842b-145">The first line in the Dockerfile designates the base image using the [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) instruction.</span></span> <span data-ttu-id="d842b-146">İleri [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) dosyasında uygulama varlıklarından kopyalar **yayımlama** klasörü kök klasöre kapsayıcı ve son; ayarı [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) Görüntü durumlarını bu kapsayıcı başlatıldığında, çalıştırılacak komut veya uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="d842b-146">Next, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) in the file copies the application assets from the **publish** folder to root folder of the container and last; setting the [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) of the image states that this is the command or application that will run when the container starts.</span></span> 

## <a name="creating-the-image"></a><span data-ttu-id="d842b-147">Görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="d842b-147">Creating the image</span></span>
<span data-ttu-id="d842b-148">Docker görüntü oluşturmak için aşağıdaki kodu eklenen *build.ps1* komut dosyası.</span><span class="sxs-lookup"><span data-stu-id="d842b-148">In order to create the Docker image, the following code is added to the *build.ps1* script.</span></span> <span data-ttu-id="d842b-149">Komut dosyasını çalıştırdığınızda `console-random-answer-generator` görüntü tanımlanan MSBuild gelen derlenmiş varlıklar kullanılarak oluşturulan [uygulama oluşturma](#building-the-application) bölümü.</span><span class="sxs-lookup"><span data-stu-id="d842b-149">When the script is run, the `console-random-answer-generator` image is created using the assets compiled from MSBuild defined in the [Building the application](#building-the-application) section.</span></span>

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

<span data-ttu-id="d842b-150">Komut dosyası kullanarak çalıştırmak `.\build.ps1` PowerShell komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="d842b-150">Run the script using `.\build.ps1` from the PowerShell command prompt.</span></span>

<span data-ttu-id="d842b-151">Yapı tamamlandığında kullanarak `docker images` komutu bir komut satırından veya PowerShell komut isteminde; görüntü oluşturulan ve çalıştırılmaya hazır olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d842b-151">When the build is complete, using the `docker images` command from a command line or PowerShell prompt; you'll see that the image is created and ready to be run.</span></span>

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a><span data-ttu-id="d842b-152">Kapsayıcı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d842b-152">Running the container</span></span>
<span data-ttu-id="d842b-153">Kapsayıcı Docker komutları kullanarak komut satırından başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d842b-153">You can start the container from the command line using the Docker commands.</span></span>

```
docker run console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="d842b-154">Çıktı</span><span class="sxs-lookup"><span data-stu-id="d842b-154">The output is</span></span>

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

<span data-ttu-id="d842b-155">Çalıştırırsanız `docker ps -a` komutunu Powershell'den, kapsayıcı hala var olduğundan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d842b-155">If you run the `docker ps -a` command from PowerShell, you can see that the container still exists.</span></span>

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

<span data-ttu-id="d842b-156">Durum sütununda "yaklaşık bir dakika önce", gösterir uygulama tam ve kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="d842b-156">The STATUS column shows at "About a minute ago", the application was complete and could be shut down.</span></span> <span data-ttu-id="d842b-157">Komutu yüzlerce kez çalıştırırsanız kapsayıcıları sol statik yapması ile yüzlerce olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d842b-157">If the command was run a hundred times, there would be a hundred containers left static with no work to do.</span></span> <span data-ttu-id="d842b-158">İşlerini yapmak için ideal işlemi başına senaryoda oldu ve kapatma veya temizleme.</span><span class="sxs-lookup"><span data-stu-id="d842b-158">In the beginning scenario the ideal operation was to do the work and shutdown or cleanup.</span></span> <span data-ttu-id="d842b-159">Bu iş akışı gerçekleştirmek için ekleme `--rm` için seçenek `docker run` komutu kapsayıcı kaldırmak hemen `Exited` sinyali aldı.</span><span class="sxs-lookup"><span data-stu-id="d842b-159">To accomplish that workflow, adding the `--rm` option to the `docker run` command will remove the container as soon as the `Exited` signal is received.</span></span>

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="d842b-160">Bu seçenekle komutu çalıştırmak ve çıktısını arayan `docker ps -a` dikkat edin; komutu kapsayıcı kimliği ( `Environment.MachineName`) listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="d842b-160">Running the command with this option and then looking at the output of `docker ps -a` command; notice that the container id (the `Environment.MachineName`) is not in the list.</span></span>

### <a name="running-the-container-using-powershell"></a><span data-ttu-id="d842b-161">PowerShell kullanarak kapsayıcı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d842b-161">Running the container using PowerShell</span></span>
<span data-ttu-id="d842b-162">Örnek proje dosyalarında bulunmaktadır bir *run.ps1* bağımsız değişkenleri kabul uygulamayı çalıştırmak için PowerShell kullanma örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d842b-162">In the sample project files there is also a *run.ps1* which is an example of how to use PowerShell to run the application accepting the arguments.</span></span>

<span data-ttu-id="d842b-163">Çalıştırmak için PowerShell'i açın ve aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d842b-163">To run, open PowerShell and use the following command:</span></span>

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a><span data-ttu-id="d842b-164">Özet</span><span class="sxs-lookup"><span data-stu-id="d842b-164">Summary</span></span>
<span data-ttu-id="d842b-165">Yalnızca bir Dockerfile ekleme ve uygulama yayımlama, .NET Framework'te konsol uygulamaları containerize ve artık birden çok örneği, temiz Başlat ve Durdur ve daha fazla Windows Server 2016 yetenekleri herhangi yapmadan çalıştıran avantajlarından yararlanmak uygulama kodu hiç değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d842b-165">Just by adding a Dockerfile and publishing the application, you can containerize your .NET Framework console applications and now take the advantage of running multiple instances, clean start and stop and more Windows Server 2016 capabilities without making any changes to the application code at all.</span></span>

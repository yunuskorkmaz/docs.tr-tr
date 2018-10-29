---
title: Docker'da çalışan konsol uygulamaları
description: Mevcut bir .NET Framework konsol uygulamasını alıp Windows Docker kapsayıcısında çalıştırmayı öğrenin.
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: bf21357efc234ea99836b190ce34c70f2644ea6a
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374761"
---
# <a name="running-console-applications-in-windows-containers"></a><span data-ttu-id="2cc8c-103">Windows kapsayıcıları içinde çalışan konsol uygulamaları</span><span class="sxs-lookup"><span data-stu-id="2cc8c-103">Running console applications in Windows containers</span></span>

<span data-ttu-id="2cc8c-104">Konsol uygulamaları, birçok farklı amaçla kullanılır; Basit bir durum için uzun süre çalışan görüntüsünün sorgulamasını işleme görevlerini.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-104">Console applications are used for many purposes; from simple querying of a status to long running document image processing tasks.</span></span> <span data-ttu-id="2cc8c-105">Herhangi bir durumda, başlatın ve bu uygulamaları ölçeklendirme olanağı karşılanmadığı sınırlamaları donanım satın almalar, başlangıç sürelerinde veya birden fazla örneği çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-105">In any case, the ability to start up and scale these applications are met with limitations of hardware acquisitions, startup times or running multiple instances.</span></span>

<span data-ttu-id="2cc8c-106">Docker ve Windows Server'ı kullanmak için konsol uygulamaları taşıma kapsayıcıları tanır bu uygulamaları etkinleştirme işlemi ve ardından kapatma düzgün bir şekilde gerçekleştirmek için temiz bir durumdan başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-106">Moving your console applications to use Docker and Windows Server containers allows for starting these applications from a clean state, enabling them to perform the operation and then shutdown cleanly.</span></span> <span data-ttu-id="2cc8c-107">Bu konuda, bir Windows konsol uygulamaya taşımak için gerekli olan adımları kapsayıcı tabanlı ve bir PowerShell Betiği kullanarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-107">This topic will show the steps needed to move a console application to a Windows based container and start it using a PowerShell script.</span></span>

<span data-ttu-id="2cc8c-108">Örnek konsol uygulaması, bu durumda bir soru bağımsız değişken alır ve rastgele bir yanıt döndürür basit bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-108">The sample console application is a simple example which takes an argument, a question in this case, and returns a random answer.</span></span> <span data-ttu-id="2cc8c-109">Bu sürebilir bir `customer_id` ve bunların vergileri işlemek veya ilişkin bir küçük resim oluşturma bir `image_url` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-109">This could take a `customer_id` and process their taxes, or create a thumbnail for an `image_url` argument.</span></span>

<span data-ttu-id="2cc8c-110">Yanıt yanı sıra `Environment.MachineName` yerel olarak ve bir Windows kapsayıcı uygulaması çalıştıran arasındaki farkı göstermek için yanıta eklenir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-110">In addition to the answer, the `Environment.MachineName` has been added to the response to show the difference between running the application locally and in a Windows container.</span></span> <span data-ttu-id="2cc8c-111">Uygulamayı yerel olarak çalışırken, yerel makine adını döndürülmesi gerektiğini ve bir Windows kapsayıcısı içinde çalışırken kapsayıcı oturum kimliği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-111">When running the application locally, your local machine name should be returned and when running in a Windows Container; the container session id is returned.</span></span>

<span data-ttu-id="2cc8c-112">[Tam bir örnek](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) dotnet/samples deposuna github'da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-112">The [complete example](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) is available in the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="2cc8c-113">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="2cc8c-113">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="2cc8c-114">Uygulamanız bir kapsayıcıya taşıma çalışmaya başlamadan önce koşulları bazı Docker ile ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-114">You need to be familiar with some Docker terms before you begin working on moving your application to a container.</span></span>

> <span data-ttu-id="2cc8c-115">A *Docker görüntüsü* ortam için işletim sistemi (OS), sistem bileşenleri ve uygulamaları dahil olmak üzere, çalışan bir kapsayıcı tanımlar salt okunur bir şablondur.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-115">A *Docker image* is a read-only template that defines the environment for a running container, including the operating system (OS), system components, and application(s).</span></span>

<span data-ttu-id="2cc8c-116">Docker görüntüleri bir önemli özelliği, görüntüleri bir temel görüntüden oluşur.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-116">One important feature of Docker images is that images are composed from a base image.</span></span> <span data-ttu-id="2cc8c-117">Her yeni görüntüyü küçük bir özellik kümesi için mevcut bir görüntü ekler.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-117">Each new image adds a small set of features to an existing image.</span></span> 

> <span data-ttu-id="2cc8c-118">A *Docker kapsayıcısı* görüntü, çalışan bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-118">A *Docker container* is a running instance of an image.</span></span> 

<span data-ttu-id="2cc8c-119">Bir uygulama, çok sayıda kapsayıcı içinde aynı görüntü çalıştırarak ölçeklendirin.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-119">You scale an application by running the same image in many containers.</span></span>
<span data-ttu-id="2cc8c-120">Kavramsal olarak, bu birden çok konak aynı uygulamayı çalıştırmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-120">Conceptually, this is similar to running the same application in multiple hosts.</span></span>

<span data-ttu-id="2cc8c-121">Okuyarak Docker mimarisi hakkında daha fazla bilgi edinebilirsiniz [Docker'a genel bakış](https://docs.docker.com/engine/understanding-docker/) Docker sitesinde.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-121">You can learn more about the Docker architecture by reading the [Docker Overview](https://docs.docker.com/engine/understanding-docker/) on the Docker site.</span></span> 

<span data-ttu-id="2cc8c-122">Konsol uygulamanızı taşımak birkaç adım bir konudur.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-122">Moving your console application is a matter of a few steps.</span></span>

1. [<span data-ttu-id="2cc8c-123">Uygulamayı oluşturun</span><span class="sxs-lookup"><span data-stu-id="2cc8c-123">Build the application</span></span>](#building-the-application)
1. [<span data-ttu-id="2cc8c-124">Görüntü için bir Dockerfile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2cc8c-124">Creating a Dockerfile for the image</span></span>](#creating-the-dockerfile)
1. [<span data-ttu-id="2cc8c-125">Derleme ve Docker kapsayıcısını çalıştırma işlemi</span><span class="sxs-lookup"><span data-stu-id="2cc8c-125">Process to build and run the Docker container</span></span>](#creating-the-image)

## <a name="prerequisites"></a><span data-ttu-id="2cc8c-126">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2cc8c-126">Prerequisites</span></span>
<span data-ttu-id="2cc8c-127">Windows kapsayıcıları desteklenmektedir [Windows 10 Yıldönümü güncelleştirmesi](https://www.microsoft.com/en-us/software-download/windows10/) veya [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span><span class="sxs-lookup"><span data-stu-id="2cc8c-127">Windows containers are supported on [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) or [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span></span>

> [!NOTE]
><span data-ttu-id="2cc8c-128">Windows Server 2016'yı kullanıyorsanız, Docker için Windows Yükleyici özelliği etkin değildir bu yana kapsayıcılar el ile etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-128">If you are using Windows Server 2016, you must enable containers manually since the Docker for Windows installer will not enable the feature.</span></span> <span data-ttu-id="2cc8c-129">Tüm güncelleştirmeler için işletim sistemi çalıştıran ve ardından yönergeleri izleyin emin [kapsayıcı konak dağıtımı](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) kapsayıcıları ve Docker özellikleri yüklemek için makale.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-129">Make sure all updates have run for the OS and then follow the instructions from the [Container Host Deployment](/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server) article to install the containers and Docker features.</span></span>

<span data-ttu-id="2cc8c-130">Docker için Windows, sürüm 1.12 desteklemek için Beta 26 veya üzeri Windows kapsayıcıları olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-130">You need to have Docker for Windows, version 1.12 Beta 26 or higher to support Windows containers.</span></span> <span data-ttu-id="2cc8c-131">Varsayılan olarak, Docker, Linux tabanlı kapsayıcılar sağlar; Windows kapsayıcıları için Docker sistem tepsisindeki simgeye sağ tıklayarak geçin ve seçin **Windows kapsayıcılarına geç**.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-131">By default, Docker enables Linux based containers; switch to Windows containers by right clicking the Docker icon in the system tray and select **Switch to Windows containers**.</span></span> <span data-ttu-id="2cc8c-132">Docker değiştirme işlemi çalışır ve bir yeniden başlatma gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-132">Docker will run the process to change and a restart may be required.</span></span>

![Windows kapsayıcıları](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a><span data-ttu-id="2cc8c-134">Uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="2cc8c-134">Building the application</span></span>
<span data-ttu-id="2cc8c-135">Yükleyici, FTP veya dosya paylaşımı konsol uygulamaları genellikle dağıtılmış dağıtım.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-135">Typically console applications are distributed through an installer, FTP, or File Share deployment.</span></span> <span data-ttu-id="2cc8c-136">Bir kapsayıcıya dağıtılırken varlıkları derlenir ve Docker görüntüsü oluşturulduğunda kullanılabilecek bir konuma aşamalı gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-136">When deploying to a container, the assets need to be compiled and staged to a location that can be used when the Docker image is created.</span></span>

<span data-ttu-id="2cc8c-137">İçinde *build.ps1*, betikte [MSBuild](/visualstudio/msbuild/msbuild) varlıkları oluşturma görevini tamamlamak için bir uygulama derlemek için.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-137">In *build.ps1*, the script uses [MSBuild](/visualstudio/msbuild/msbuild) to compile the application to complete the task of building the assets.</span></span> <span data-ttu-id="2cc8c-138">Gerekli varlıkları sonlandırmak için MSBuild'e geçirilen birkaç parametre yok.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-138">There are a few parameters passed to MSBuild to finalize the needed assets.</span></span> <span data-ttu-id="2cc8c-139">Proje dosyası veya derlenecek çözüm, konum adı için çıktı ve son olarak yapılandırma (yayınlama veya hata ayıklama).</span><span class="sxs-lookup"><span data-stu-id="2cc8c-139">The name of the project file or solution to be compiled, the location for the output and finally the configuration (Release or Debug).</span></span>

<span data-ttu-id="2cc8c-140">Çağrısında `Invoke-MSBuild` `OutputPath` ayarlanır **yayımlama** ve `Configuration` kümesine **yayın**.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-140">In the call to `Invoke-MSBuild` the `OutputPath` is set to **publish** and  `Configuration` set to **Release**.</span></span> 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj -p:OutputPath=.\publish -p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a><span data-ttu-id="2cc8c-141">Dockerfile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2cc8c-141">Creating the Dockerfile</span></span>
<span data-ttu-id="2cc8c-142">.NET Framework uygulamasına Konsolu için kullanılan temel görüntü `microsoft/windowsservercore`, üzerinde genel kullanıma açık [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span><span class="sxs-lookup"><span data-stu-id="2cc8c-142">The base image used for a console .NET Framework application is `microsoft/windowsservercore`, publicly available on [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span></span> <span data-ttu-id="2cc8c-143">Temel görüntü en az bir Windows Server 2016, .NET Framework 4.6.2 yüklenmesini içerir ve Windows kapsayıcıları için temel işletim sistemi görüntüsü görev yapar.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-143">The base image contains a minimal installation of Windows Server 2016, .NET Framework 4.6.2 and serves as the base OS image for Windows Containers.</span></span>

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
<span data-ttu-id="2cc8c-144">Temel görüntüyü kullanarak Dockerfile ilk satırı atayan [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) yönergesi.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-144">The first line in the Dockerfile designates the base image using the [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) instruction.</span></span> <span data-ttu-id="2cc8c-145">Ardından, [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) dosyasında uygulama varlıklarından kopyalar **yayımlama** klasörünü kök klasöre kapsayıcı ve son; ayarı [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) Görüntü durumlarını söz konusu komut veya kapsayıcı başlatıldığında çalıştırılacak uygulama budur.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-145">Next, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) in the file copies the application assets from the **publish** folder to root folder of the container and last; setting the [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) of the image states that this is the command or application that will run when the container starts.</span></span> 

## <a name="creating-the-image"></a><span data-ttu-id="2cc8c-146">Görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="2cc8c-146">Creating the image</span></span>
<span data-ttu-id="2cc8c-147">Docker görüntüsünü oluşturmak için aşağıdaki kodu eklenir *build.ps1* betiği.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-147">In order to create the Docker image, the following code is added to the *build.ps1* script.</span></span> <span data-ttu-id="2cc8c-148">Betiği çalıştırdığınızda `console-random-answer-generator` görüntü MSBuild içinde tanımlanan gelen derlenmiş varlıklar kullanılarak oluşturulan [uygulama oluşturma](#building-the-application) bölümü.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-148">When the script is run, the `console-random-answer-generator` image is created using the assets compiled from MSBuild defined in the [Building the application](#building-the-application) section.</span></span>

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

<span data-ttu-id="2cc8c-149">Betik kullanarak çalıştırma `.\build.ps1` PowerShell komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-149">Run the script using `.\build.ps1` from the PowerShell command prompt.</span></span>

<span data-ttu-id="2cc8c-150">Derleme tamamlandığında kullanarak `docker images` komutu bir komut satırı ya da PowerShell isteminden; görüntü oluşturulur ve çalıştırılmaya hazır olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-150">When the build is complete, using the `docker images` command from a command line or PowerShell prompt; you'll see that the image is created and ready to be run.</span></span>

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a><span data-ttu-id="2cc8c-151">Kapsayıcı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2cc8c-151">Running the container</span></span>
<span data-ttu-id="2cc8c-152">Kapsayıcı Docker komutlarını kullanarak komut satırından başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-152">You can start the container from the command line using the Docker commands.</span></span>

```
docker run console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="2cc8c-153">Çıktı</span><span class="sxs-lookup"><span data-stu-id="2cc8c-153">The output is</span></span>

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

<span data-ttu-id="2cc8c-154">Çalıştırırsanız `docker ps -a` komutunu Powershell'den kapsayıcının hala olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-154">If you run the `docker ps -a` command from PowerShell, you can see that the container still exists.</span></span>

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

<span data-ttu-id="2cc8c-155">Durum sütununda "yaklaşık bir dakika önce", gösterir uygulama tam ve kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-155">The STATUS column shows at "About a minute ago", the application was complete and could be shut down.</span></span> <span data-ttu-id="2cc8c-156">Komutu yüzlerce kez çalıştırırsanız yapması ile kapsayıcıları sol statik bir yüz olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-156">If the command was run a hundred times, there would be a hundred containers left static with no work to do.</span></span> <span data-ttu-id="2cc8c-157">Başlangıç senaryosunda, işlerini gerçekleştirmek için ideal işlemin tamamlandığını ve kapatma veya temizleme.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-157">In the beginning scenario the ideal operation was to do the work and shutdown or cleanup.</span></span> <span data-ttu-id="2cc8c-158">O iş akışını gerçekleştirmek için ekleme `--rm` seçeneğini `docker run` komutu, kapsayıcı kaldırılır hemen sonra `Exited` sinyali aldı.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-158">To accomplish that workflow, adding the `--rm` option to the `docker run` command will remove the container as soon as the `Exited` signal is received.</span></span>

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="2cc8c-159">Bu seçenek ile çalıştırarak ve ardından çıktısına arayarak `docker ps -a` komut; dikkat kapsayıcı kimliği ( `Environment.MachineName`) listesinde değil.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-159">Running the command with this option and then looking at the output of `docker ps -a` command; notice that the container id (the `Environment.MachineName`) is not in the list.</span></span>

### <a name="running-the-container-using-powershell"></a><span data-ttu-id="2cc8c-160">PowerShell kullanarak kapsayıcı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2cc8c-160">Running the container using PowerShell</span></span>
<span data-ttu-id="2cc8c-161">Örnek proje dosyalarında olduğu da bir *run.ps1* bağımsız değişkenleri kabul eden uygulamayı çalıştırmak için PowerShell kullanma örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-161">In the sample project files there is also a *run.ps1* which is an example of how to use PowerShell to run the application accepting the arguments.</span></span>

<span data-ttu-id="2cc8c-162">Çalıştırmak için PowerShell'i açın ve aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2cc8c-162">To run, open PowerShell and use the following command:</span></span>

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a><span data-ttu-id="2cc8c-163">Özet</span><span class="sxs-lookup"><span data-stu-id="2cc8c-163">Summary</span></span>
<span data-ttu-id="2cc8c-164">Yalnızca bir Dockerfile ekleme ve uygulama yayımlama, .NET Framework konsol uygulamalarınızı kapsayıcılı hale getirme ve artık birden çok örneği, temiz bir başlangıç ve durdurma ve daha fazla Windows Server 2016 özellikleri, herhangi yapmadan çalıştıran avantajından faydalanın hiç uygulama koduna değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2cc8c-164">Just by adding a Dockerfile and publishing the application, you can containerize your .NET Framework console applications and now take the advantage of running multiple instances, clean start and stop and more Windows Server 2016 capabilities without making any changes to the application code at all.</span></span>

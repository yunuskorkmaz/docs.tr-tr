---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamalarının geliştirilmesi için "iç döngü" iş akışını öğrenin.
ms.date: 02/15/2019
ms.openlocfilehash: 615cfd08f46609c4e100ea3e72b541fe2c1ae62a
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989018"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="ed469-103">Docker uygulamaları için iç döngü geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="ed469-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="ed469-104">Tüm DevOps döngüsünü kapsayan dış döngü iş akışını tetiklemeden önce, her geliştiricinin makinesinde başlar, uygulamanın kendisini kodlar, tercih ettikleri dilleri veya platformları kullanır ve yerel olarak test eder (Şekil 4-21).</span><span class="sxs-lookup"><span data-stu-id="ed469-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="ed469-105">Ancak her durumda, hangi dili, çerçeveyi veya platformları seçerseniz seçin, ortak önemli bir noktanız olacak.</span><span class="sxs-lookup"><span data-stu-id="ed469-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="ed469-106">Bu özel iş akışında, Docker kapsayıcılarını her zaman yerel olarak geliştiriyor ve test ediyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="ed469-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Bir iç döngü dev ortam kavramını gösteren diyagram.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="ed469-108">**Şekil 4-21**.</span><span class="sxs-lookup"><span data-stu-id="ed469-108">**Figure 4-21**.</span></span> <span data-ttu-id="ed469-109">İç-döngü geliştirme bağlamı</span><span class="sxs-lookup"><span data-stu-id="ed469-109">Inner-loop development context</span></span>

<span data-ttu-id="ed469-110">Docker görüntüsünün kapsayıcısı veya örneği şu bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ed469-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="ed469-111">İşletim sistemi seçimi (örneğin, Bir Linux dağıtımı veya Windows)</span><span class="sxs-lookup"><span data-stu-id="ed469-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="ed469-112">Geliştirici tarafından eklenen dosyalar (örneğin, uygulama ikilileri)</span><span class="sxs-lookup"><span data-stu-id="ed469-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="ed469-113">Yapılandırma (örneğin, ortam ayarları ve bağımlılıklar)</span><span class="sxs-lookup"><span data-stu-id="ed469-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="ed469-114">Docker tarafından hangi süreçlerin yürütülacağına yönelik talimatlar</span><span class="sxs-lookup"><span data-stu-id="ed469-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="ed469-115">İşlem olarak Docker'ı kullanan iç döngü geliştirme iş akışını ayarlayabilirsiniz (sonraki bölümde açıklanmıştır).</span><span class="sxs-lookup"><span data-stu-id="ed469-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="ed469-116">Ortamı ayarlamak için ilk adımların dahil olmadığını, çünkü yalnızca bir kez yapmanız gerektiğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ed469-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="ed469-117">Visual Studio Code ve Docker CLI kullanarak Docker konteyneriçinde tek bir uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed469-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="ed469-118">Uygulamalar kendi hizmetlerinizden ve ek kitaplıklardan (bağımlılıklar) oluşur.</span><span class="sxs-lookup"><span data-stu-id="ed469-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="ed469-119">Şekil 4-22, bir Docker uygulaması inşa ederken genellikle gerçekleştirmeniz gereken temel adımları ve ardından her adımın ayrıntılı açıklamalarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed469-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Kapsayıcı bir uygulama oluşturmak için gereken yedi adımı gösteren diyagram.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="ed469-121">**Şekil 4-22**.</span><span class="sxs-lookup"><span data-stu-id="ed469-121">**Figure 4-22**.</span></span> <span data-ttu-id="ed469-122">Docker CLI kullanarak Docker konteyner uygulamaları için yaşam döngüsü için üst düzey iş akışı</span><span class="sxs-lookup"><span data-stu-id="ed469-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="ed469-123">Adım 1: Visual Studio Code'da kodlamaya başlayın ve ilk uygulama/hizmet taban çizginizi oluşturun</span><span class="sxs-lookup"><span data-stu-id="ed469-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="ed469-124">Uygulamanızı geliştirme şekliniz Docker olmadan yaptığınız avekçe benzer.</span><span class="sxs-lookup"><span data-stu-id="ed469-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="ed469-125">Aradaki fark, geliştirirken, uygulamanızı veya yerel ortamınıza yerleştirilen Docker kapsayıcıları içinde çalışan hizmetleri (Linux VM veya Windows gibi) dağıtıyor ve test ediyor olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ed469-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="ed469-126">**Yerel ortamınızı ayarlama**</span><span class="sxs-lookup"><span data-stu-id="ed469-126">**Setting up your local environment**</span></span>

<span data-ttu-id="ed469-127">Mac ve Windows için Docker'ın en son sürümleriyle Docker uygulamalarını geliştirmek her zamankinden daha kolay ve kurulum çok kolay.</span><span class="sxs-lookup"><span data-stu-id="ed469-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="ed469-128">Windows için Docker'ı ayarlama yla <https://docs.docker.com/docker-for-windows/>ilgili talimatlar için .</span><span class="sxs-lookup"><span data-stu-id="ed469-128">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="ed469-129">Mac için Docker kurma talimatları için, gidin. <https://docs.docker.com/docker-for-mac/></span><span class="sxs-lookup"><span data-stu-id="ed469-129">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="ed469-130">Buna ek olarak, Docker CLI kullanırken uygulamanızı gerçekten geliştirebilmeniz için bir kod düzenleyicisine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ed469-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="ed469-131">Microsoft, Windows, Linux ve macOS'ta desteklenen hafif bir kod düzenleyicisi olan Visual Studio Code'u sağlar ve IntelliSense'e [birçok dil](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python ve en modern diller) desteği sağlar, [hata ayıklama,](https://code.visualstudio.com/Docs/editor/debugging)Git ve uzantıları [desteği](https://code.visualstudio.com/docs/extensions/overview) [ile tümleştirme](https://code.visualstudio.com/Docs/editor/versioncontrol) sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed469-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="ed469-132">Bu editör macOS ve Linux geliştiricileri için harika bir uyum.</span><span class="sxs-lookup"><span data-stu-id="ed469-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="ed469-133">Windows'da Visual Studio'u da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="ed469-134">Windows, Linux veya macOS için Visual Studio Kodu <https://code.visualstudio.com/docs/setup/setup-overview/>yükleme yönergeleri için.</span><span class="sxs-lookup"><span data-stu-id="ed469-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="ed469-135">Mac için Docker kurma talimatları için, gidin. <https://docs.docker.com/docker-for-mac/></span><span class="sxs-lookup"><span data-stu-id="ed469-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="ed469-136">Docker CLI ile çalışabilir ve herhangi bir kod düzenleyicisini kullanarak kodunuzu yazabilirsiniz, ancak `Dockerfile` `docker-compose.yml` Docker uzantısı ile Visual Studio Code'u kullanmak çalışma alanınızda yazmanızı ve dosyaları kolayca yazmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ed469-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="ed469-137">Ayrıca, altında Docker CLI kullanarak Docker komutlarını yürütmek için Visual Studio Code IDE'den görevleri ve komut ları çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="ed469-138">VS Code için Docker uzantısı aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="ed469-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="ed469-139">Otomatik `Dockerfile` `docker-compose.yml` ve dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="ed469-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="ed469-140">Sözdizimi vurgulama ve gezinme `docker-compose.yml` `Dockerfile` ipuçları ve dosyalar</span><span class="sxs-lookup"><span data-stu-id="ed469-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="ed469-141">IntelliSense (tamamlamalar) `Dockerfile` `docker-compose.yml` için ve dosyalar</span><span class="sxs-lookup"><span data-stu-id="ed469-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="ed469-142">Dosyalar için `Dockerfile` linting (hatalar ve uyarılar)</span><span class="sxs-lookup"><span data-stu-id="ed469-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="ed469-143">En yaygın Docker komutları için Komut Paleti (F1) tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="ed469-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="ed469-144">Görüntüleri ve Kapsayıcıları yönetmek için Explorer tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="ed469-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="ed469-145">DockerHub ve Azure Konteyner Kayıt Şirketlerinden görüntüleri Azure Uygulama Hizmetine dağıtma</span><span class="sxs-lookup"><span data-stu-id="ed469-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="ed469-146">Docker uzantısını yüklemek için Ctrl+Shift+P `ext install`tuşuna basın, ardından Market uzantı listesini açmak için Uzantıyı Yükle komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ed469-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="ed469-147">Ardından, sonuçları filtrelemek için **docker** yazın ve ardından Şekil 4-23'te belirtildiği gibi Docker Destek uzantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="ed469-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![VS Kodu için Docker uzantısıgörünümü.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="ed469-149">**Şekil 4-23**.</span><span class="sxs-lookup"><span data-stu-id="ed469-149">**Figure 4-23**.</span></span> <span data-ttu-id="ed469-150">Docker Uzantısının Visual Studio Koduna Yüklenmesi</span><span class="sxs-lookup"><span data-stu-id="ed469-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="ed469-151">Adım 2: Varolan bir görüntüyle ilgili bir DockerFile oluşturun (.NET Core, Node.js ve Ruby gibi düz işletim sistemi veya dev ortamlar)</span><span class="sxs-lookup"><span data-stu-id="ed469-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="ed469-152">Oluşturulacak özel `DockerFile` görüntü başına ve dağıtılmak üzere konteyner başına bir görüntü gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed469-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="ed469-153">Uygulamanız tek bir özel hizmetten oluşuyorsa, tek `DockerFile`bir özel hizmete ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ed469-153">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="ed469-154">Ancak uygulamanız birden çok hizmet (mikro hizmetler mimarisinde olduğu gibi) oluşuyorsa, her hizmet için bir hizmete `Dockerfile` ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ed469-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="ed469-155">Uygulama `DockerFile` veya hizmetin kök klasörüne sık sık yerleştirilir ve Docker'ın bu uygulamayı veya hizmeti nasıl kurup çalıştırılabildiğini bilmesi için gerekli komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="ed469-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="ed469-156">Kodunuzu (node.js, .NET Core, vb.) birlikte oluşturabilir `DockerFile` ve projenize ekleyebilirsiniz veya çevreye yeniyseniz aşağıdaki İpucu'na göz atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="ed469-157">Docker kapsayıcılarınızla ilgili `Dockerfile` dosyaları ve dosyaları `docker-compose.yml` kullanırken size rehberlik etmek için Docker uzantısını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="ed469-158">Sonunda, muhtemelen bu araç olmadan bu tür dosyaları yazacağım, ancak Docker uzantısı kullanarak öğrenme eğrisi hızlandıracak iyi bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="ed469-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="ed469-159">Şekil 4-24'te, VS Kodu için Docker Uzantısı kullanılarak docker-compose dosyasının nasıl eklendirilebildiğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-159">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![VS Code için Docker uzantısı konsol görünümü.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="ed469-161">**Şekil 4-24**.</span><span class="sxs-lookup"><span data-stu-id="ed469-161">**Figure 4-24**.</span></span> <span data-ttu-id="ed469-162">**Docker dosyaları Çalışma Alanı komutuna Docker dosyaları ekle** kullanılarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ed469-162">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="ed469-163">DockerFile eklediğinizde, hangi temel Docker görüntüsünü kullanacağınızı (kullanmak `FROM mcr.microsoft.com/dotnet/core/aspnet`gibi) belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-163">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="ed469-164">Özel resminizi genellikle [Docker Hub kayıt defterindeki](https://hub.docker.com/) herhangi bir resmi depodan aldığınız temel görüntünün üzerine [(.NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) veya [Node.js](https://hub.docker.com/_/node/)için bir resim gibi) oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="ed469-164">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="ed469-165">***Mevcut resmi Docker resmini kullanma***</span><span class="sxs-lookup"><span data-stu-id="ed469-165">***Use an existing official Docker image***</span></span>

<span data-ttu-id="ed469-166">Sürüm numarası olan bir dil yığınının resmi deposunun kullanılması, aynı dil özelliklerinin tüm makinelerde (geliştirme, test ve üretim dahil) kullanılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed469-166">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="ed469-167">Aşağıda bir .NET Core kapsayıcı için örnek DockerFile:</span><span class="sxs-lookup"><span data-stu-id="ed469-167">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="ed469-168">Bu durumda, görüntü sürüm `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`2.2 resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok kemer) satırına göre dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ed469-168">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="ed469-169">(Bu konu hakkında daha fazla bilgi için, [ASP.NET Core Docker Resim](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sayfasına ve [.NET Core Docker Resim](https://hub.docker.com/_/microsoft-dotnet-core/) sayfasına bakın).</span><span class="sxs-lookup"><span data-stu-id="ed469-169">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="ed469-170">DockerFile'da, Docker'a çalışma zamanında kullanacağınız TCP bağlantı noktasını (bağlantı noktası 80 gibi) dinlemesi için talimat verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-170">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="ed469-171">Kullandığınız dile ve çerçeveye bağlı olarak Dockerfile'da ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-171">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="ed469-172">Örneğin, `ENTRYPOINT` satır Docker'a `["dotnet", "MySingleContainerWebApp.dll"]` bir .NET Core uygulaması çalıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="ed469-172">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="ed469-173">.NET uygulamasını oluşturmak ve çalıştırmak için SDK`dotnet CLI`ve .NET Core CLI () kullanıyorsanız, bu ayar farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ed469-173">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="ed469-174">Burada önemli nokta, ENTRYPOINT satırı ve diğer ayarların uygulamanız için seçtiğiniz dile ve platforma bağlı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="ed469-174">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="ed469-175">.NET Core uygulamaları için Docker görüntüleri oluşturma hakkında <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>daha fazla bilgi için .</span><span class="sxs-lookup"><span data-stu-id="ed469-175">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="ed469-176">Kendi resimlerinizi oluşturma hakkında daha <https://docs.docker.com/engine/tutorials/dockerimages/>fazla bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="ed469-176">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="ed469-177">**Çok kemerli görüntü depolarını kullanma**</span><span class="sxs-lookup"><span data-stu-id="ed469-177">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="ed469-178">Repo'daki tek bir görüntü adı, Linux görüntüsü ve Windows görüntüsü gibi platform türevleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ed469-178">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="ed469-179">Bu özellik, Microsoft (temel görüntü oluşturucular) gibi satıcıların birden çok platformu (linux ve Windows) kapsayacak şekilde tek bir repo oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ed469-179">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="ed469-180">Örneğin, Docker Hub kayıt defterinde bulunan [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) deposu, linux ve Windows Nano Server için aynı görüntü adını kullanarak destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed469-180">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="ed469-181">Bir Windows ana bilgisayardan [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) görüntüsünü çekmek Windows varyantını çekerken, linux ana bilgisayardan aynı görüntü adını çekmek Linux varyantını çeker.</span><span class="sxs-lookup"><span data-stu-id="ed469-181">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="ed469-182">***Temel resminizi sıfırdan oluşturun***</span><span class="sxs-lookup"><span data-stu-id="ed469-182">***Create your base image from scratch***</span></span>

<span data-ttu-id="ed469-183">Docker'ın bu [makalesinde](https://docs.docker.com/engine/userguide/eng-image/baseimages/) açıklandığı gibi kendi Docker taban resminizi sıfırdan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-183">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="ed469-184">Docker ile yeni başlıyorsanız, bu senaryo sizin için en iyisi değildir, ancak kendi temel görüntünüzün belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-184">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="ed469-185">Adım 3: Özel Docker resimlerinizi oluşturun ve hizmetinizi bu görüntülere katıştırma</span><span class="sxs-lookup"><span data-stu-id="ed469-185">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="ed469-186">Uygulamanızı oluşturan her özel hizmet için ilgili bir resim oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed469-186">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="ed469-187">Uygulamanız tek bir hizmet veya web uygulamasından oluşuyorsa, tek bir görüntüye ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ed469-187">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="ed469-188">"Dış döngü DevOps iş akışı" dikkate alınarak, kaynak kodunuzu bir Git deposuna (Sürekli Tümleştirme) itdiğinizde görüntüler otomatik bir yapı işlemi tarafından oluşturulur, böylece görüntüler kaynak kodunuzdan bu küresel ortamda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ed469-188">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="ed469-189">Ancak bu dış döngü rotasına gitmeyi düşünmeden önce, Docker uygulamasının kaynak kontrol sistemine (Git, vb.) düzgün çalışmayan kodu itmemeleri için doğru çalıştığından emin olmalıyız.</span><span class="sxs-lookup"><span data-stu-id="ed469-189">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="ed469-190">Bu nedenle, her geliştiricinin önce yerel olarak test etmek ve tam bir özelliği zorlamak veya kaynak denetim sistemine değiştirmek isteyene kadar geliştirmeye devam etmek için tüm iç döngü işlemini yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed469-190">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="ed469-191">Yerel ortamınızda ve DockerFile'ı kullanmak için Şekil 4-25'te gösterildiği gibi docker build komutunu `docker-compose up --build` kullanabilirsiniz (çeşitli kapsayıcılar/hizmetlerden oluşan uygulamalar için de çalıştırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="ed469-191">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Docker build komutunun konsol çıktısını gösteren ekran görüntüsü.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="ed469-193">**Şekil 4-25**.</span><span class="sxs-lookup"><span data-stu-id="ed469-193">**Figure 4-25**.</span></span> <span data-ttu-id="ed469-194">Çalışan docker yapı</span><span class="sxs-lookup"><span data-stu-id="ed469-194">Running docker build</span></span>

<span data-ttu-id="ed469-195">İsteğe bağlı olarak, `docker build` doğrudan proje klasöründen çalışan yerine, önce çalıştır `dotnet publish` komutunu kullanarak gereken .NET `docker build`kitaplıkları ile dağıtılabilir bir klasör oluşturabilir ve sonra çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-195">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="ed469-196">Bu örnek, adında `cesardl/netcore-webapi-microservice-docker:first` bir Docker`:first` görüntüsü oluşturur (belirli bir sürüm gibi bir etikettir).</span><span class="sxs-lookup"><span data-stu-id="ed469-196">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="ed469-197">Birkaç kapsayıcı ile oluşan Docker uygulaması için oluşturmanız gereken her özel görüntü için bu adımı atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-197">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="ed469-198">Mevcut görüntüleri Şekil 4-26'da gösterildiği gibi docker görüntüleri komutunu kullanarak yerel deponuzda (geliştirme makinenizde) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-198">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Varolan görüntüleri gösteren komut docker görüntüleri konsol çıkışı.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="ed469-200">**Şekil 4-26**.</span><span class="sxs-lookup"><span data-stu-id="ed469-200">**Figure 4-26**.</span></span> <span data-ttu-id="ed469-201">Docker görüntülerini kullanarak mevcut görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="ed469-201">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="ed469-202">Adım 4: Birden fazla hizmetiçeren oluşturulmuş bir Docker uygulaması oluştururken servislerinizi docker-compose.yml olarak tanımlayın</span><span class="sxs-lookup"><span data-stu-id="ed469-202">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="ed469-203">Dosyayla, `docker-compose.yml` bir sonraki adım bölümünde açıklanan dağıtım komutlarıyla oluşturulmuş bir uygulama olarak dağıtılacak ilgili hizmetler kümesini tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-203">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="ed469-204">Bu dosyayı ana veya kök çözüm klasörünüzde oluşturun; bu `docker-compose.yml` dosyada gösterilenbenzer içeriğe sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="ed469-204">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

<span data-ttu-id="ed469-205">Bu özel durumda, bu dosya iki hizmeti tanımlar: web hizmeti (özel hizmetiniz) ve redis hizmeti (popüler bir önbellek hizmeti).</span><span class="sxs-lookup"><span data-stu-id="ed469-205">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="ed469-206">Her hizmet bir konteyner olarak dağıtılacak, bu yüzden her biri için bir beton Docker görüntü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed469-206">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="ed469-207">Bu özel web hizmeti için, görüntüaşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ed469-207">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="ed469-208">Geçerli dizindeki DockerFile'dan yapı</span><span class="sxs-lookup"><span data-stu-id="ed469-208">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="ed469-209">Konteynerüzerindeki açık port 80'i ana makinedeki 81 portuna iletin</span><span class="sxs-lookup"><span data-stu-id="ed469-209">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="ed469-210">Proje dizinini kapsayıcının içindeki /koda ana bilgisayara monte ederek görüntüyü yeniden oluşturmanıza gerek kalmadan kodu değiştirmenizi mümkün kılar</span><span class="sxs-lookup"><span data-stu-id="ed469-210">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="ed469-211">Redis hizmetine web hizmetini bağla</span><span class="sxs-lookup"><span data-stu-id="ed469-211">Link the web service to the redis service</span></span>

<span data-ttu-id="ed469-212">Redis hizmeti, Docker Hub kayıt defterinden çıkarılan [en son genel redis görüntüsünü](https://hub.docker.com/_/redis/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="ed469-212">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="ed469-213">[redis](https://redis.io/) sunucu tarafı uygulamaları için popüler bir önbellek sistemidir.</span><span class="sxs-lookup"><span data-stu-id="ed469-213">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="ed469-214">Adım 5: Docker uygulamanızı oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="ed469-214">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="ed469-215">Uygulamanızda yalnızca tek bir kapsayıcı varsa, yalnızca Docker Host'unuza (VM veya fiziksel sunucu) dağıtarak uygulamanızı çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed469-215">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="ed469-216">Ancak, uygulamanız birden çok hizmetten oluşuyorsa, uygulamayı da *oluşturmanız*gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed469-216">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="ed469-217">Farklı seçenekleri görelim.</span><span class="sxs-lookup"><span data-stu-id="ed469-217">Let's see the different options.</span></span>

<span data-ttu-id="ed469-218">***Seçenek A: Tek bir kapsayıcı veya hizmet çalıştırma***</span><span class="sxs-lookup"><span data-stu-id="ed469-218">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="ed469-219">Docker çalışmasını kullanarak Docker görüntüsünü burada gösterildiği gibi çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ed469-219">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="ed469-220">Bu özel dağıtım için, 80 bağlantı noktasına gönderilen istekleri iç bağlantı noktası 5000'e yönlendireceğiz.</span><span class="sxs-lookup"><span data-stu-id="ed469-220">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="ed469-221">Şimdi uygulama ana bilgisayar düzeyinde dış bağlantı noktası 80 dinliyor.</span><span class="sxs-lookup"><span data-stu-id="ed469-221">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="ed469-222">***Seçenek B: Çoklu kapsayıcı uygulaması oluşturma ve çalıştırma***</span><span class="sxs-lookup"><span data-stu-id="ed469-222">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="ed469-223">Çoğu kurumsal senaryoda, Docker uygulaması birden çok hizmetlerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ed469-223">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="ed469-224">Bu gibi durumlarda, daha `docker-compose up` önce oluşturmuş olabileceğiniz docker-compose.yml dosyasını kullanan komutu (Şekil 4-27) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-224">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="ed469-225">Bu komutu çalıştıran tüm ilgili kapsayıcıları içeren oluşan bir uygulama dağıtır.</span><span class="sxs-lookup"><span data-stu-id="ed469-225">Running this command deploys a composed application with all of its related containers.</span></span>

![Docker-comto komutundan konsol çıkışı.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="ed469-227">**Şekil 4-27**.</span><span class="sxs-lookup"><span data-stu-id="ed469-227">**Figure 4-27**.</span></span> <span data-ttu-id="ed469-228">"Docker-comto up" komutunu çalıştırmanın sonuçları</span><span class="sxs-lookup"><span data-stu-id="ed469-228">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="ed469-229">Çalıştırdıktan `docker-compose up`sonra, başvurunuzu ve ilgili konteyner(ler)i Şekil 4-28'de gösterildiği gibi, VM gösteriminde gösterildiği gibi Docker Host'unuza dağıtırsınız.</span><span class="sxs-lookup"><span data-stu-id="ed469-229">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![VM çok konteyner uygulamaları çalıştırıyor.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="ed469-231">**Şekil 4-28**.</span><span class="sxs-lookup"><span data-stu-id="ed469-231">**Figure 4-28**.</span></span> <span data-ttu-id="ed469-232">Docker konteynerleri dağıtılan VM</span><span class="sxs-lookup"><span data-stu-id="ed469-232">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="ed469-233">Adım 6: Docker uygulamanızı test edin (yerel olarak, yerel CD VM'nizde)</span><span class="sxs-lookup"><span data-stu-id="ed469-233">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="ed469-234">Bu adım, uygulamanızın ne yaptığına bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="ed469-234">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="ed469-235">Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web API "Hello World"de, DockerFile'da belirtilen TCP bağlantı noktasını sağlayarak hizmete erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed469-235">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="ed469-236">Localhost açık değilse, hizmetinize gitmek için, bu komutu kullanarak makinenin IP adresini bulun:</span><span class="sxs-lookup"><span data-stu-id="ed469-236">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="ed469-237">Docker ana bilgisayarda bir tarayıcı açın ve bu siteye gidin; Şekil 4-29'da gösterildiği gibi uygulamanızın/hizmetin izinin çalıştığını görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed469-237">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Localhost/API/values'ten gelen yanıtın tarayıcı görünümü.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="ed469-239">**Şekil 4-29**.</span><span class="sxs-lookup"><span data-stu-id="ed469-239">**Figure 4-29**.</span></span> <span data-ttu-id="ed469-240">Docker uygulamanızı localhost kullanarak yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="ed469-240">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="ed469-241">Port 80'i kullandığını, ancak dahili olarak 5000 portuna yönlendirildiğini unutmayın, çünkü daha önce `docker run`açıklandığı gibi bu şekilde dağıtıldı.</span><span class="sxs-lookup"><span data-stu-id="ed469-241">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="ed469-242">Bunu terminalden CURL kullanarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-242">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="ed469-243">Windows'daki Docker yüklemesinde, varsayılan IP Şekil 4-30'da belirtildiği gibi 10.0.75.1'dir.</span><span class="sxs-lookup"><span data-stu-id="ed469-243">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Kıvrılma http://10.0.75.1/API/values ile elde konsol çıkışı](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="ed469-245">**Şekil 4-30**.</span><span class="sxs-lookup"><span data-stu-id="ed469-245">**Figure 4-30**.</span></span> <span data-ttu-id="ed469-246">CURL kullanarak docker uygulamasını yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="ed469-246">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="ed469-247">**Docker üzerinde çalışan bir konteyner hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="ed469-247">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="ed469-248">Visual Studio Code, Node.js ve .NET Core kapsayıcıları gibi diğer platformları kullanıyorsanız Docker hata ayıklama destekler.</span><span class="sxs-lookup"><span data-stu-id="ed469-248">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="ed469-249">Bir sonraki bölümde açıklandığı gibi, Windows veya Mac için Visual Studio'yu kullanırken Docker'da .NET Core veya .NET Framework kapsayıcılarını hata ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed469-249">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="ed469-250">Node.js Docker konteynerlerini hata ayıklama hakkında <https://blog.docker.com/2016/07/live-debugging-docker/> <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="ed469-250">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ed469-251">[Önceki](docker-apps-development-environment.md)
>[Sonraki](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="ed469-251">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>

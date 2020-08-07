---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamaları için "Inner-loop" geliştirme iş akışı hakkında bilgi edinin.
ms.date: 08/06/2020
ms.openlocfilehash: bf837ab53fff2b53cf141b2e621d484cff9b6889
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916154"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="d875d-103">Docker uygulamaları için iç döngü geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="d875d-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="d875d-104">Tüm DevOps döngüsünü kapsayan dış döngü iş akışını tetiklemeden önce, hepsi her bir geliştirici makinesinde başlar, tercih edilen dillerini veya platformları kullanarak uygulamanın kendisini kodlayıp yerel olarak test edin (Şekil 4-21).</span><span class="sxs-lookup"><span data-stu-id="d875d-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="d875d-105">Ancak her durumda, sizin seçtiğiniz dil, çerçeve veya platformlardan bağımsız olarak, genel olarak önemli bir noktaya sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d875d-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="d875d-106">Bu belirli iş akışında, Docker kapsayıcılarını her zaman başka bir ortamda geliştirmekte ve test eteceğiz, ancak yerel olarak.</span><span class="sxs-lookup"><span data-stu-id="d875d-106">In this specific workflow, you're always developing and testing Docker containers in no other environments, but locally.</span></span>

![Bir iç döngü geliştirme ortamı kavramını gösteren diyagram.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="d875d-108">**Şekil 4-21**.</span><span class="sxs-lookup"><span data-stu-id="d875d-108">**Figure 4-21**.</span></span> <span data-ttu-id="d875d-109">İç döngü geliştirme bağlamı</span><span class="sxs-lookup"><span data-stu-id="d875d-109">Inner-loop development context</span></span>

<span data-ttu-id="d875d-110">Bir Docker görüntüsünün kapsayıcısı veya örneği şu bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d875d-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="d875d-111">Bir işletim sistemi seçimi (örneğin, bir Linux dağıtımı veya Windows)</span><span class="sxs-lookup"><span data-stu-id="d875d-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="d875d-112">Geliştirici tarafından eklenen dosyalar (örneğin, uygulama ikilileri)</span><span class="sxs-lookup"><span data-stu-id="d875d-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="d875d-113">Yapılandırma (örneğin, ortam ayarları ve bağımlılıklar)</span><span class="sxs-lookup"><span data-stu-id="d875d-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="d875d-114">Docker tarafından hangi işlemlerin çalıştırılacağını gösteren yönergeler</span><span class="sxs-lookup"><span data-stu-id="d875d-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="d875d-115">İşlem olarak Docker kullanan iç döngü geliştirme iş akışını (sonraki bölümde açıklanmıştır) ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="d875d-116">Yalnızca bir kez yapmanız gerektiğinden, ortamı ayarlamaya yönelik ilk adımların dahil edilmediğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d875d-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="d875d-117">Visual Studio Code ve Docker CLı kullanarak bir Docker kapsayıcısı içinde tek bir uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="d875d-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="d875d-118">Uygulamalar, kendi hizmetinizden ve ek kitaplıklardan (bağımlılıklar) oluşur.</span><span class="sxs-lookup"><span data-stu-id="d875d-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="d875d-119">Şekil 4-22, genellikle bir Docker uygulaması oluştururken gerçekleştirmeniz gereken temel adımları gösterir ve ardından her adımın ayrıntılı açıklamalarını izler.</span><span class="sxs-lookup"><span data-stu-id="d875d-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Kapsayıcılı bir uygulama oluşturmak için gereken yedi adımı gösteren diyagram.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="d875d-121">**Şekil 4-22**.</span><span class="sxs-lookup"><span data-stu-id="d875d-121">**Figure 4-22**.</span></span> <span data-ttu-id="d875d-122">Docker CLı kullanan Docker Kapsayıcılı uygulamalar için yaşam döngüsü için üst düzey iş akışı</span><span class="sxs-lookup"><span data-stu-id="d875d-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="d875d-123">1. Adım: Visual Studio Code kodlama başlatın ve ilk uygulamanızı/hizmet temelinizi oluşturun</span><span class="sxs-lookup"><span data-stu-id="d875d-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="d875d-124">Uygulamanızı geliştirme yönteminiz, Docker olmadan yaptığınız yönteme benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d875d-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="d875d-125">Bu fark, geliştirme sırasında uygulamanızı veya hizmetlerinizi yerel ortamınıza (Linux VM veya Windows gibi) yerleştirilmiş olan Docker Kapsayıcıları içinde çalışan, dağıtmanıza ve test etdiğinize göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="d875d-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="d875d-126">**Yerel ortamınızı ayarlama**</span><span class="sxs-lookup"><span data-stu-id="d875d-126">**Setting up your local environment**</span></span>

<span data-ttu-id="d875d-127">Mac ve Windows için Docker Desktop 'ın en son sürümlerinde, Docker uygulamalarının geliştirilmesi her zamankinden daha kolay olur ve Kurulum basittir.</span><span class="sxs-lookup"><span data-stu-id="d875d-127">With the latest versions of Docker Desktop for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="d875d-128">Windows için Docker Desktop 'ı ayarlamaya ilişkin yönergeler için adresine gidin <https://docs.docker.com/docker-for-windows/> .</span><span class="sxs-lookup"><span data-stu-id="d875d-128">For instructions on setting up Docker Desktop for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
> <span data-ttu-id="d875d-129">Mac için Docker Desktop 'ı ayarlamaya ilişkin yönergeler için adresine gidin <https://docs.docker.com/docker-for-mac/> .</span><span class="sxs-lookup"><span data-stu-id="d875d-129">For instructions on setting up Docker Desktop for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="d875d-130">Ayrıca, Docker CLı kullanırken uygulamanızı geliştirebilmeniz için bir kod düzenleyicisine gerek duyarsınız.</span><span class="sxs-lookup"><span data-stu-id="d875d-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="d875d-131">Microsoft, Windows, Linux ve macOS 'ta desteklenen bir basit kod Düzenleyicisi olan Visual Studio Code sağlar ve IntelliSense 'i [birçok dil](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .net, Go, Java, Ruby, Python ve en modern diller), [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), [Git](https://code.visualstudio.com/Docs/editor/versioncontrol) ve [Uzantılar desteğiyle tümleştirme desteği](https://code.visualstudio.com/docs/extensions/overview)sunan bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="d875d-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="d875d-132">Bu düzenleyici macOS ve Linux geliştiricileri için harika bir uyum.</span><span class="sxs-lookup"><span data-stu-id="d875d-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="d875d-133">Windows 'da, Visual Studio 'Yu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="d875d-134">Windows, Linux veya macOS için Visual Studio Code yükleme yönergeleri için adresine gidin <https://code.visualstudio.com/docs/setup/setup-overview/> .</span><span class="sxs-lookup"><span data-stu-id="d875d-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="d875d-135">Mac için Docker 'ı ayarlamaya ilişkin yönergeler için adresine gidin <https://docs.docker.com/docker-for-mac/> .</span><span class="sxs-lookup"><span data-stu-id="d875d-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="d875d-136">Docker CLı ile çalışabilir ve herhangi bir kod Düzenleyicisi kullanarak kodunuzu yazabilirsiniz, ancak Docker uzantısıyla Visual Studio Code kullanmak, `Dockerfile` çalışma alanınızdaki yazma ve dosyaları daha kolay hale getirir `docker-compose.yml` .</span><span class="sxs-lookup"><span data-stu-id="d875d-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="d875d-137">Ayrıca, altındaki Docker CLı kullanarak Docker komutlarını yürütmek için Visual Studio Code IDE 'den görevler ve betikler çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="d875d-138">VS Code için Docker uzantısı aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="d875d-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="d875d-139">Otomatik `Dockerfile` ve `docker-compose.yml` dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="d875d-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="d875d-140">`docker-compose.yml`Ve dosyaları için sözdizimi vurgulama ve üzerine gelme ipuçları `Dockerfile`</span><span class="sxs-lookup"><span data-stu-id="d875d-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="d875d-141">`Dockerfile`Ve dosyaları Için IntelliSense (tamamlama `docker-compose.yml` )</span><span class="sxs-lookup"><span data-stu-id="d875d-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="d875d-142">Dosyalar için linme (hatalar ve uyarılar) `Dockerfile`</span><span class="sxs-lookup"><span data-stu-id="d875d-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="d875d-143">En yaygın Docker komutları için komut paleti (F1) Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="d875d-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="d875d-144">Görüntüleri ve kapsayıcıları yönetmek için Gezgin tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="d875d-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="d875d-145">DockerHub ve Azure Container kayıt defterlerinden görüntüleri Azure App Service için dağıtma</span><span class="sxs-lookup"><span data-stu-id="d875d-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="d875d-146">Docker uzantısını yüklemek için CTRL + SHIFT + P tuşlarına basın, yazın `ext install` ve sonra da Market uzantı listesini açmak Için uzantı Install komutunu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d875d-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="d875d-147">Sonra, sonuçları filtrelemek için **Docker** yazın ve Şekil 4-23 ' de gösterildiği gibi Docker destek uzantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="d875d-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![VS Code için Docker uzantısının görünümü.](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="d875d-149">**Şekil 4-23**.</span><span class="sxs-lookup"><span data-stu-id="d875d-149">**Figure 4-23**.</span></span> <span data-ttu-id="d875d-150">Visual Studio Code Docker uzantısını yükleme</span><span class="sxs-lookup"><span data-stu-id="d875d-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="d875d-151">2. Adım: var olan bir görüntüyle ilgili bir DockerFile oluşturma (.NET Core, Node.js ve Ruby gibi basit işletim sistemleri veya geliştirme ortamları)</span><span class="sxs-lookup"><span data-stu-id="d875d-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="d875d-152">Dağıtılması için bir `DockerFile` özel görüntü ve dağıtılacak kapsayıcı başına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="d875d-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="d875d-153">Uygulamanız tek bir özel hizmetten yapılırsa, tek yapmanız gerekir `DockerFile` .</span><span class="sxs-lookup"><span data-stu-id="d875d-153">If your app is made up of single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="d875d-154">Ancak uygulamanız birden çok hizmetten oluşuyorsa (bir mikro hizmet mimarisinde olduğu gibi), hizmet başına bir tane gerekir `Dockerfile` .</span><span class="sxs-lookup"><span data-stu-id="d875d-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="d875d-155">`DockerFile`Genellikle uygulamanızın veya hizmetinizin kök klasörüne yerleştirilir ve Docker 'ın o uygulamayı veya hizmeti nasıl ayarlayacağını ve çalıştıracağını bilmesi için gerekli komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="d875d-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="d875d-156">Kodunuzu oluşturup `DockerFile` projenize (node.js, .NET Core vb.) birlikte ekleyebilirsiniz, ya da ortama yeni başladıysanız aşağıdaki ipucuna göz atın.</span><span class="sxs-lookup"><span data-stu-id="d875d-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="d875d-157">Docker `Dockerfile` kapsayıcılarınız ile ilgili ve dosyalarını kullanırken size rehberlik etmek Için Docker uzantısını kullanabilirsiniz `docker-compose.yml` .</span><span class="sxs-lookup"><span data-stu-id="d875d-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="d875d-158">Sonuç olarak, bu tür dosyaları bu araç olmadan yazarsınız, ancak Docker uzantısının kullanılması, öğrenme eğinizi hızlandırmaya yönelik iyi bir başlangıç noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="d875d-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="d875d-159">Şekil 4-24 ' de Docker dosyalarını bir projeye ekleme adımlarını VS Code için Docker uzantısını kullanarak görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d875d-159">In Figure 4-24, you can see the steps to add the docker files to a project by using the Docker Extension for VS Code:</span></span>

1. <span data-ttu-id="d875d-160">Komut paletini açın, "**Docker**" yazın ve "**çalışma alanına Docker dosyaları Ekle**" seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d875d-160">Open the command palette, type "**docker**" and select "**Add Docker Files to Workspace**".</span></span>
2. <span data-ttu-id="d875d-161">Uygulama platformunu seçin (ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="d875d-161">Select Application Platform (ASP.NET Core)</span></span>
3. <span data-ttu-id="d875d-162">Işletim sistemini seçin (Linux)</span><span class="sxs-lookup"><span data-stu-id="d875d-162">Select Operating System (Linux)</span></span>
4. <span data-ttu-id="d875d-163">İsteğe bağlı Docker Compose dosyaları Ekle</span><span class="sxs-lookup"><span data-stu-id="d875d-163">Include optional Docker Compose files</span></span>
5. <span data-ttu-id="d875d-164">Yayımlanacak bağlantı noktalarını girin (80, 443)</span><span class="sxs-lookup"><span data-stu-id="d875d-164">Enter ports to publish (80, 443)</span></span>
6. <span data-ttu-id="d875d-165">Projeyi seçin</span><span class="sxs-lookup"><span data-stu-id="d875d-165">Select the project</span></span>

![Docker uzantılı Docker dosyaları ekleme adımları](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="d875d-167">**Şekil 4-24**.</span><span class="sxs-lookup"><span data-stu-id="d875d-167">**Figure 4-24**.</span></span> <span data-ttu-id="d875d-168">**Çalışma alanına Docker dosyaları Ekle** komutu kullanılarak Docker dosyaları eklendi</span><span class="sxs-lookup"><span data-stu-id="d875d-168">Docker files added using the **Add Docker files to Workspace** command</span></span>

<span data-ttu-id="d875d-169">Bir DockerFile eklediğinizde, kullanacağınız temel Docker görüntüsünü (kullanma gibi `FROM mcr.microsoft.com/dotnet/core/aspnet` ) belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-169">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="d875d-170">Genellikle, [Docker Hub kayıt defterinde](https://hub.docker.com/) ( [.NET Core için bir görüntü](https://hub.docker.com/_/microsoft-dotnet-core/) veya [Node.jsiçin ](https://hub.docker.com/_/node/)bir görüntü gibi) herhangi bir resmi depodan aldığınız bir temel görüntünün en üstünde özel görüntünüzü oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d875d-170">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

> [!TIP]
> <span data-ttu-id="d875d-171">Uygulamanızdaki her proje için bu yordamı tekrarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d875d-171">You'll have to repeat this procedure for every project in your application.</span></span> <span data-ttu-id="d875d-172">Ancak, uzantı ilk kez oluşturulan Docker-Compose dosyasını geçersiz kılacak.</span><span class="sxs-lookup"><span data-stu-id="d875d-172">However, the extension will ask to overwrite the generated docker-compose file after the first time.</span></span> <span data-ttu-id="d875d-173">Üzerine yazılmaması gerekir, bu nedenle uzantı, Docker-Compose çalıştırmadan önce el ile birleştirebilmeniz için ayrı Docker-Compose dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d875d-173">You should reply to not overwrite it, so the extension creates separate docker-compose files, that you can then merge by hand, prior to running docker-compose.</span></span>

<span data-ttu-id="d875d-174">**_Mevcut bir resmi Docker görüntüsünü kullanma_**</span><span class="sxs-lookup"><span data-stu-id="d875d-174">**_Use an existing official Docker image_**</span></span>

<span data-ttu-id="d875d-175">Sürüm numarasına sahip bir dil yığınının resmi deposunu kullanmak, tüm makinelerde (geliştirme, test ve üretim dahil) aynı dil özelliklerinin kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d875d-175">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="d875d-176">Aşağıda .NET Core kapsayıcısı için örnek bir DockerFile verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d875d-176">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

<span data-ttu-id="d875d-177">Bu durumda, görüntü, satıra göre resmi ASP.NET Core Docker görüntüsünün 3,1 sürümünü (Linux ve Windows için çoklu mimari) temel alır `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` .</span><span class="sxs-lookup"><span data-stu-id="d875d-177">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="d875d-178">(Bu konu hakkında daha fazla bilgi için, [ASP.NET Core Docker görüntü](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sayfasına ve [.NET Core Docker görüntü](https://hub.docker.com/_/microsoft-dotnet-core/) sayfasına bakın).</span><span class="sxs-lookup"><span data-stu-id="d875d-178">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="d875d-179">DockerFile 'da, Docker 'ın çalışma zamanında kullanacağınız TCP bağlantı noktasını (bağlantı noktası 80 veya 443) dinleyebildiğini da söyleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-179">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80 or 443).</span></span>

<span data-ttu-id="d875d-180">Kullanmakta olduğunuz dile ve çerçeveye bağlı olarak Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="d875d-181">Örneğin, çizgi, `ENTRYPOINT` `["dotnet", "WebMvcApplication.dll"]` Docker 'A .NET Core uygulaması çalıştırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="d875d-181">For instance, the `ENTRYPOINT` line with `["dotnet", "WebMvcApplication.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="d875d-182">`dotnet CLI`.NET uygulamasını derlemek ve çalıştırmak IÇIN SDK ve .NET Core CLI () kullanıyorsanız, bu ayar farklı olur.</span><span class="sxs-lookup"><span data-stu-id="d875d-182">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="d875d-183">Buradaki anahtar noktası, GIRIŞ noktası satırı ve diğer ayarların, uygulamanız için seçtiğiniz dile ve platforma bağlı olmasına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d875d-183">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="d875d-184">.NET Core uygulamaları için Docker görüntüleri oluşturma hakkında daha fazla bilgi için adresine gidin <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images> .</span><span class="sxs-lookup"><span data-stu-id="d875d-184">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="d875d-185">Kendi görüntülerinizi oluşturma hakkında daha fazla bilgi edinmek için adresine gidin <https://docs.docker.com/engine/tutorials/dockerimages/> .</span><span class="sxs-lookup"><span data-stu-id="d875d-185">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="d875d-186">**Çoklu mimari görüntü depoları kullanma**</span><span class="sxs-lookup"><span data-stu-id="d875d-186">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="d875d-187">Depodaki tek bir görüntü adı, Linux görüntüsü ve Windows görüntüsü gibi platform türevlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d875d-187">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="d875d-188">Bu özellik, Microsoft (temel görüntü oluşturucuları) gibi satıcıların birden çok platformu (yani, Linux ve Windows) kapsayacak şekilde tek bir depo oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d875d-188">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="d875d-189">Örneğin, Docker Hub kayıt defterinde bulunan [DotNet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) deposu, aynı görüntü adı kullanılarak Linux ve Windows nano Server için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="d875d-189">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="d875d-190">Bir Windows ana bilgisayarının [DotNet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) görüntüsünü çekmek, Windows türevini çeker, ancak aynı görüntü adının bir Linux ana bilgisayardan çekmesinde Linux varyantı çekilir.</span><span class="sxs-lookup"><span data-stu-id="d875d-190">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="d875d-191">**_Sıfırdan taban görüntünüzü oluşturma_**</span><span class="sxs-lookup"><span data-stu-id="d875d-191">**_Create your base image from scratch_**</span></span>

<span data-ttu-id="d875d-192">Docker 'daki bu [makalede](https://docs.docker.com/engine/userguide/eng-image/baseimages/) açıklandığı gibi, kendi Docker temel görüntünüzü sıfırdan oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-192">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="d875d-193">Bu senaryo muhtemelen yalnızca Docker ile başlıyorsanız sizin için en iyi yöntem değildir, ancak kendi temel görüntünüzün belirli bitlerini ayarlamak istiyorsanız bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-193">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="d875d-194">3. Adım: hizmetinizi katıştırma özel Docker görüntülerinizi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d875d-194">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="d875d-195">Uygulamanızı içeren her bir özel hizmet için ilgili bir görüntü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d875d-195">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="d875d-196">Uygulamanız tek bir hizmetten veya Web uygulamasından yapılırsa yalnızca tek bir görüntüye ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="d875d-196">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="d875d-197">"Dış döngü DevOps iş akışını" hesaba katdığınızda,, kaynak kodunuzu bir git deposuna (sürekli tümleştirme) gönderdiğinizde görüntüler otomatik derleme işlemi tarafından oluşturulur. bu nedenle, görüntüler kaynak kodunuzla ilgili genel ortamda oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d875d-197">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="d875d-198">Ancak, bu dış döngü yoluna gitmeden önce, Docker uygulamasının doğru şekilde çalıştığından emin olmanız gerekir. böylece, kaynak denetim sistemine (git, vb.) düzgün çalışmayan bir kod gönderemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="d875d-198">But before you consider going to that outer-loop route, you need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="d875d-199">Bu nedenle, her geliştiricinin ilk olarak yerel olarak test etmesi için tüm iç döngü sürecini yapması ve tam bir özellik göndermek veya kaynak denetim sistemine geçiş yapmak istemeleriyle geliştirmeye devam etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d875d-199">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="d875d-200">Yerel ortamınızda bir görüntü oluşturmak ve DockerFile 'ı kullanmak için, Şekil 4-25 ' de gösterildiği gibi Docker Build komutunu kullanabilirsiniz. Bu, resmi sizin için etiketleyen ve basit bir komutla uygulamadaki tüm hizmetlere ait görüntüleri derlemedir.</span><span class="sxs-lookup"><span data-stu-id="d875d-200">To create an image in your local environment and using the DockerFile, you can use the docker build command, as shown in Figure 4-25, because it already tags the image for you and builds the images for all services in the application with a simple command.</span></span>

![Docker-Compose derleme komutunun konsol çıkışını gösteren ekran görüntüsü.](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="d875d-202">**Şekil 4-25**.</span><span class="sxs-lookup"><span data-stu-id="d875d-202">**Figure 4-25**.</span></span> <span data-ttu-id="d875d-203">Docker derlemesini çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d875d-203">Running docker build</span></span>

<span data-ttu-id="d875d-204">İsteğe bağlı olarak, proje klasöründen doğrudan çalıştırmak yerine `docker build` , Çalıştır komutunu kullanarak gerekli .NET kitaplıkları ile dağıtılabilir bir klasör oluşturabilir `dotnet publish` ve sonra öğesini çalıştırabilirsiniz `docker build` .</span><span class="sxs-lookup"><span data-stu-id="d875d-204">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="d875d-205">Bu örnek, adıyla bir Docker görüntüsü oluşturur `explore-docker-vscode/webapi:latest` ( `:latest` belirli bir sürüm gibi bir etikettir).</span><span class="sxs-lookup"><span data-stu-id="d875d-205">This example creates a Docker image with the name `explore-docker-vscode/webapi:latest` (`:latest` is a tag, like a specific version).</span></span> <span data-ttu-id="d875d-206">Bu adımı, çeşitli kapsayıcılarla oluşturulmuş Docker uygulamanız için oluşturmanız gereken her özel görüntü için gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-206">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span> <span data-ttu-id="d875d-207">Bununla birlikte, bunu kullanarak bunu daha kolay bir şekilde yapacağız `docker-compose` .</span><span class="sxs-lookup"><span data-stu-id="d875d-207">However, we'll see in the next section that it's easier to do this using `docker-compose`.</span></span>

<span data-ttu-id="d875d-208">Mevcut görüntüleri, `docker images` şekil 4-26 ' de gösterildiği gibi, komutunu kullanarak yerel deponuzda (geliştirme makineniz) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-208">You can find the existing images in your local repository (your development machine) by using the `docker images` command, as illustrated in Figure 4-26.</span></span>

![Mevcut görüntüleri gösteren komut Docker görüntülerinin konsol çıktısı.](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="d875d-210">**Şekil 4-26**.</span><span class="sxs-lookup"><span data-stu-id="d875d-210">**Figure 4-26**.</span></span> <span data-ttu-id="d875d-211">Docker görüntülerini kullanarak mevcut görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d875d-211">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="d875d-212">4. Adım: birden çok hizmet ile oluşturulmuş bir Docker uygulaması oluştururken hizmetlerinizi Docker-Compose. yml 'de tanımlama</span><span class="sxs-lookup"><span data-stu-id="d875d-212">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="d875d-213">Dosyası ile `docker-compose.yml` , bir sonraki adım bölümünde açıklanan dağıtım komutlarıyla oluşturulmuş bir uygulama olarak dağıtılacak bir dizi ilgili hizmet tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-213">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="d875d-214">Ana veya kök çözüm klasörünüzde bu dosyayı oluşturun; Bu dosyada gösterilene benzer içeriğe sahip olmalıdır `docker-compose.yml` :</span><span class="sxs-lookup"><span data-stu-id="d875d-214">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

<span data-ttu-id="d875d-215">Bu durumda, bu dosya üç hizmeti tanımlar: Web API hizmeti (özel hizmetiniz), bir Web uygulaması ve Redsıs hizmeti (popüler önbellek hizmeti).</span><span class="sxs-lookup"><span data-stu-id="d875d-215">In this particular case, this file defines three services: the web API service (your custom service), a web application, and the Redis service (a popular cache service).</span></span> <span data-ttu-id="d875d-216">Her hizmet bir kapsayıcı olarak dağıtılır, bu nedenle her biri için somut bir Docker görüntüsü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d875d-216">Each service will be deployed as a container, so you need to use a concrete Docker image for each.</span></span> <span data-ttu-id="d875d-217">Bu uygulama için:</span><span class="sxs-lookup"><span data-stu-id="d875d-217">For this particular application:</span></span>

- <span data-ttu-id="d875d-218">Web API hizmeti, dizindeki DockerFile dosyasından oluşturulur `src/WebApi/Dockerfile` .</span><span class="sxs-lookup"><span data-stu-id="d875d-218">The web API service is built from the DockerFile in the `src/WebApi/Dockerfile` directory.</span></span>

- <span data-ttu-id="d875d-219">51080 ana bilgisayar bağlantı noktası, kapsayıcıda bulunan 80 numaralı bağlantı noktasına iletilir `webapi` .</span><span class="sxs-lookup"><span data-stu-id="d875d-219">The host port 51080 is forwarded to the exposed port 80 on the `webapi` container.</span></span>

- <span data-ttu-id="d875d-220">Web API hizmeti Redsıs hizmetine bağlıdır</span><span class="sxs-lookup"><span data-stu-id="d875d-220">The web API service depends on the Redis service</span></span>

- <span data-ttu-id="d875d-221">Web uygulaması, iç adresini kullanarak Web API hizmetine erişir: `http://webapi` .</span><span class="sxs-lookup"><span data-stu-id="d875d-221">The web application accesses the web API service using the internal address: `http://webapi`.</span></span>

- <span data-ttu-id="d875d-222">Redsıs hizmeti, Docker Hub kayıt defterinden çekilen [en son ortak redo görüntüsünü](https://hub.docker.com/_/redis/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="d875d-222">The Redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="d875d-223">[Redsıs](https://redis.io/) , sunucu tarafı uygulamalar için popüler bir önbellek sistemidir.</span><span class="sxs-lookup"><span data-stu-id="d875d-223">[Redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="d875d-224">5. Adım: Docker uygulamanızı derleme ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d875d-224">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="d875d-225">Uygulamanızda yalnızca tek bir kapsayıcı varsa, bunu yalnızca Docker konağına (VM veya fiziksel sunucu) dağıtarak çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d875d-225">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="d875d-226">Ancak, uygulamanız birden çok hizmetten yapılırsa, _bunu_da oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d875d-226">However, if your app is made up of multiple services, you need to _compose it_, too.</span></span> <span data-ttu-id="d875d-227">Farklı seçenekleri görelim.</span><span class="sxs-lookup"><span data-stu-id="d875d-227">Let's see the different options.</span></span>

<span data-ttu-id="d875d-228">**_Seçenek A: tek bir kapsayıcı veya hizmet çalıştırma_**</span><span class="sxs-lookup"><span data-stu-id="d875d-228">**_Option A: Run a single container or service_**</span></span>

<span data-ttu-id="d875d-229">Docker görüntüsünü, burada gösterildiği gibi Docker Run komutunu kullanarak çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d875d-229">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 50080:80 explore-docker-vscode/webapp:latest
```

<span data-ttu-id="d875d-230">Bu dağıtım için, ana bilgisayarda 50080 numaralı bağlantı noktasına gönderilen istekleri iç bağlantı noktası 80 ' e yeniden yönlentireceğiz.</span><span class="sxs-lookup"><span data-stu-id="d875d-230">For this particular deployment, we'll be redirecting requests sent to port 50080 on the host to the internal port 80.</span></span>

<span data-ttu-id="d875d-231">**_Seçenek B: çok kapsayıcılı bir uygulama oluşturma ve çalıştırma_**</span><span class="sxs-lookup"><span data-stu-id="d875d-231">**_Option B: Compose and run a multiple-container application_**</span></span>

<span data-ttu-id="d875d-232">Çoğu kurumsal senaryoda, bir Docker uygulaması birden çok hizmetten oluşur.</span><span class="sxs-lookup"><span data-stu-id="d875d-232">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="d875d-233">Bu gibi durumlarda, `docker-compose up` daha önce oluşturduğunuz Docker-Compose. yıml dosyasını kullanacak olan komutunu (şekil 4-27) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-233">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you created previously.</span></span> <span data-ttu-id="d875d-234">Bu komutu çalıştırmak tüm özel görüntüleri oluşturur ve tüm ilgili kapsayıcılarıyla birlikte oluşturulan uygulamayı dağıtır.</span><span class="sxs-lookup"><span data-stu-id="d875d-234">Running this command builds all custom images and deploys the composed application with all of its related containers.</span></span>

![Docker-Compose up komutuyla konsol çıktısı.](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="d875d-236">**Şekil 4-27**.</span><span class="sxs-lookup"><span data-stu-id="d875d-236">**Figure 4-27**.</span></span> <span data-ttu-id="d875d-237">"Docker-Compose up" komutunun çalıştırılmasının sonuçları</span><span class="sxs-lookup"><span data-stu-id="d875d-237">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="d875d-238">Çalıştırdıktan sonra `docker-compose up` , uygulamanızı ve ilgili kapsayıcınızı, şekil 4-28 ' de gösterildiği gibi, sanal makine gösteriminde, Docker ana bilgisayarınıza dağıtırsınız.</span><span class="sxs-lookup"><span data-stu-id="d875d-238">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Çok Kapsayıcılı uygulamaları çalıştıran VM.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="d875d-240">**Şekil 4-28**.</span><span class="sxs-lookup"><span data-stu-id="d875d-240">**Figure 4-28**.</span></span> <span data-ttu-id="d875d-241">Docker Kapsayıcıları dağıtılan VM</span><span class="sxs-lookup"><span data-stu-id="d875d-241">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="d875d-242">6. Adım: Docker uygulamanızı test etme (yerel CD sanal makinenizde yerel olarak)</span><span class="sxs-lookup"><span data-stu-id="d875d-242">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="d875d-243">Bu adım, uygulamanızın yaptığına bağlı olarak farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="d875d-243">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="d875d-244">Tek bir kapsayıcı veya hizmet olarak dağıtılan basit bir .NET Core Web API 'SI "Merhaba Dünya", yalnızca DockerFile içinde belirtilen TCP bağlantı noktasını sağlayarak hizmete erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d875d-244">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="d875d-245">Docker konağında bir tarayıcı açın ve bu siteye gidin; Şekil 4-29 ' de gösterildiği gibi, uygulamanızı/hizmetinizi çalışır durumda görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d875d-245">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Localhost/API/değerlerden alınan yanıtın tarayıcı görünümü.](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="d875d-247">**Şekil 4-29**.</span><span class="sxs-lookup"><span data-stu-id="d875d-247">**Figure 4-29**.</span></span> <span data-ttu-id="d875d-248">Tarayıcı kullanarak Docker uygulamanızı yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="d875d-248">Testing your Docker application locally by using the browser</span></span>

<span data-ttu-id="d875d-249">50080 numaralı bağlantı noktasını kullandığını unutmayın, ancak `docker compose` daha önce açıklandığı gibi, ile birlikte dağıtılmakta olduğu gibi, dahili olarak bu bağlantı noktası 80 ' e yönlendirilmekte.</span><span class="sxs-lookup"><span data-stu-id="d875d-249">Note that it's using port 50080, but internally it's being redirected to port 80, because that's how it was deployed with `docker compose`, as explained earlier.</span></span>

<span data-ttu-id="d875d-250">Bunu, Şekil 4-30 ' de gösterildiği gibi terminalden KıVARAK tarayıcıyı kullanarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-250">You can test this by using the browser using CURL from the terminal, as depicted in Figure 4-30.</span></span>

![Şu kaynaktan alınan kıvır sonucuhttp://localhost:51080/WeatherForecast](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="d875d-252">**Şekil 4-30**.</span><span class="sxs-lookup"><span data-stu-id="d875d-252">**Figure 4-30**.</span></span> <span data-ttu-id="d875d-253">KıVRıMLı kullanarak Docker uygulamasını yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="d875d-253">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="d875d-254">**Docker üzerinde çalışan bir kapsayıcıda hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="d875d-254">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="d875d-255">Visual Studio Code, Node.js ve .NET Core kapsayıcıları gibi diğer platformları kullanıyorsanız Docker hatalarını ayıklamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="d875d-255">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="d875d-256">Ayrıca, sonraki bölümde açıklandığı gibi Windows veya Mac için Visual Studio 'Yu kullanırken Docker 'daki .NET Core veya .NET Framework kapsayıcılarında hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d875d-256">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="d875d-257">Docker Kapsayıcıları Node.js hata ayıklama hakkında daha fazla bilgi için <https://blog.docker.com/2016/07/live-debugging-docker/> bkz <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> . ve.</span><span class="sxs-lookup"><span data-stu-id="d875d-257">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="d875d-258">[Önceki](docker-apps-development-environment.md) 
>  [Sonraki](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="d875d-258">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>

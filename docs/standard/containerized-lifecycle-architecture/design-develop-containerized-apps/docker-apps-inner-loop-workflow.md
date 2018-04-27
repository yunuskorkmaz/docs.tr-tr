---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8ee1918091fe72e8606be6e7503ecd850084a4ba
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="c7715-103">Docker uygulamaları için iç döngü geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="c7715-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="c7715-104">Tüm DevOps kapsayıcı döngü dış iş akışı tetiklemeden döngüsü, tüm uygulama kodlama, kendi tercih edilen dil ya da platformlar kullanarak ve yerel olarak test her geliştiricinin makinesinde (Şekil 4-14) başlar.</span><span class="sxs-lookup"><span data-stu-id="c7715-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="c7715-105">Ancak her durumda, çok önemli bir nokta ortak hangi dil, framework ya da platformlar seçtiğiniz olsun gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="c7715-106">Bu belirli iş akışındaki her zaman geliştirdiğiniz ve Docker kapsayıcıları, ancak yerel olarak test etme.</span><span class="sxs-lookup"><span data-stu-id="c7715-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="c7715-107">Şekil 4-14: iç döngü geliştirme bağlamı</span><span class="sxs-lookup"><span data-stu-id="c7715-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="c7715-108">Kapsayıcı veya bir Docker görüntüsü örneği şu bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="c7715-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="c7715-109">Bir işletim sistemi seçim (örneğin, bir Linux dağıtım veya Windows)</span><span class="sxs-lookup"><span data-stu-id="c7715-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="c7715-110">(Örneğin, uygulama ikili dosyaları) geliştirici tarafından eklenen dosyalar</span><span class="sxs-lookup"><span data-stu-id="c7715-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="c7715-111">Yapılandırma (örneğin, ortam ayarlarını ve bağımlılıklarını)</span><span class="sxs-lookup"><span data-stu-id="c7715-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="c7715-112">Docker tarafından çalıştırmak için hangi işlemleri için yönergeler</span><span class="sxs-lookup"><span data-stu-id="c7715-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="c7715-113">Docker (sonraki bölümde açıklanan) bir işlem olarak kullanan iç döngü geliştirme iş akışı ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7715-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="c7715-114">Yalnızca bir kez yapmanız gerektiğinden ilk ortamını ayarlama adımlarını olmadığını dahil dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="c7715-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="c7715-115">Visual Studio Code ve Docker CLI kullanarak bir Docker kapsayıcısı içinde tek bir uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7715-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="c7715-116">Uygulamaları, kendi Hizmetleri artı ek kitaplıkları (bağımlılıklar) yapılır.</span><span class="sxs-lookup"><span data-stu-id="c7715-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="c7715-117">Şekil 4-15 genellikle her bir adımın ayrıntılı açıklamaları tarafından izlenen bir Docker uygulaması oluştururken gerçekleştirmesi gereken temel adımlarda gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7715-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="c7715-118">Şekil 4-15: Docker CLI kullanarak kapsayıcılı Docker uygulama yaşam döngüsü için üst düzey iş akışı</span><span class="sxs-lookup"><span data-stu-id="c7715-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="c7715-119">1. adım: Visual Studio kodda kodlama başlatmak ve ilk uygulama/hizmet taban çizgisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7715-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="c7715-120">Uygulamanızı geliştirme oldukça benzer Docker yapmak şekilde yoludur.</span><span class="sxs-lookup"><span data-stu-id="c7715-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="c7715-121">Geliştirme sırasında dağıtma ve uygulama veya Docker kapsayıcıları (örneğin, bir Linux VM veya Windows), yerel ortamınızda yerleştirilen içinde çalışan hizmetler sınama olduğundan farktır.</span><span class="sxs-lookup"><span data-stu-id="c7715-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="c7715-122">**Yerel ortamını ayarlama**</span><span class="sxs-lookup"><span data-stu-id="c7715-122">**Setting up your local environment**</span></span>

<span data-ttu-id="c7715-123">Mac ve Windows için Docker en son sürümleri, Docker uygulamaları geliştirmek için her zamankinden daha kolay ve Kurulum basittir.</span><span class="sxs-lookup"><span data-stu-id="c7715-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="c7715-124">**Daha fazla bilgi** Docker Windows için ayarlama hakkında yönergeler için Git [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="c7715-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="c7715-125">Mac için Docker ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="c7715-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="c7715-126">Ayrıca, Docker CLI kullanırken, uygulamanızın gerçekte geliştirebilirsiniz böylece bir kod düzenleyicisinde gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="c7715-127">Microsoft, Mac, Windows ve Linux desteklenir ve IntelliSense ile sağlayan bir basit bir kod düzenleyicisidir Visual Studio Code sağlar [desteklemek için çok sayıda dilleri](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Git, Java, Ruby, Python ve çoğu Modern dilleri), [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), [Git ile tümleştirme](https://code.visualstudio.com/Docs/editor/versioncontrol) ve [Uzantıları desteği](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="c7715-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="c7715-128">Mac ve Linux geliştiricileri için harika bir sığdırma düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="c7715-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="c7715-129">Windows, tam Visual Studio uygulama de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7715-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="c7715-130">**Daha fazla bilgi** Windows için Visual Studio, Mac veya Linux yükleme ile ilgili yönergeler için Git [ http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/ ](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span><span class="sxs-lookup"><span data-stu-id="c7715-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span></span>

<span data-ttu-id="c7715-131">Docker CLI ile çalışır ve herhangi bir kod düzenleyicisini kullanarak kodunuzu yazma, ancak Visual Studio Code kullanırsanız, yazar Dockerfile kolay ve docker-compose.yml dosyaları çalışma alanınızda kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c7715-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="c7715-132">Ayrıca, Docker CLI altında kullanarak ayrıntılandırılmış işlemleri çalıştıran komut dosyaları ister IDE gelen Visual Studio Code görevleri çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="c7715-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="c7715-133">Visual Studio Code yüklemeniz gerekir bir uzantı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c7715-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="c7715-134">Tuşuna Ctrl + Shift + P, bunun için türü **ext yüklemek**, ve Uzantıları'nı çalıştırın: Market uzantısı listesini getirmek için yükleme uzantısını komutu.</span><span class="sxs-lookup"><span data-stu-id="c7715-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="c7715-135">Sonra aşağıdakileri yazın **docker** sonuçlara filtre uygulamak ve ardından Dockerfile ve Docker oluşturan dosyasını (yml) destek uzantısı, Şekil 4-16'gösterildiği gibi seçin.</span><span class="sxs-lookup"><span data-stu-id="c7715-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="c7715-136">Şekil 4-16: Visual Studio kodda Docker uzantı yükleme</span><span class="sxs-lookup"><span data-stu-id="c7715-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="c7715-137">2. adım: var olan bir görüntüsünü (düz işletim sistemi veya geliştirme ortamları .NET Core, Node.js ve Ruby gibi) ilgili bir DockerFile oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7715-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="c7715-138">Uygulamanız, tek bir özel hizmet yapılırsa, bu nedenle, tek bir DockerFile gerekir, bir DockerFile dağıtılacak kapsayıcı ve oluşturulacak özel görüntü başına gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="c7715-139">Ancak, uygulamanız (örneğin, bir mikro mimarisi) birden çok hizmet oluşan bir Dockerfile hizmeti başına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="c7715-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="c7715-140">DockerFile genellikle uygulama veya hizmet kök klasörü içinde yerleştirilir ve bu Docker ayarlamak ve bu uygulamayı veya hizmeti çalıştırmak nasıl bilmesi için gerekli komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="c7715-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="c7715-141">DockerFile oluşturabilir ve kodunuzun yanı sıra projenize ekleyin (node.js, .NET Core, vb.), ya da ortama yeniyseniz, aşağıdaki ipucu göz atın.</span><span class="sxs-lookup"><span data-stu-id="c7715-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="c7715-142">Adlı bir komut satırı aracını kullanabilirsiniz [yo docker](https://github.com/Microsoft/generator-docker), hangi dosyaların projenizden dili seçin ve gerekli Docker yapılandırma dosyaları ekler iskelesini kurar.</span><span class="sxs-lookup"><span data-stu-id="c7715-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="c7715-143">Temel olarak, geliştiricilerin Başlarken yardımcı olmak için uygun DockerFile oluşturduğu docker-compose.yml ve diğer ilişkili betikler oluşturun ve Docker kapsayıcılarınızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7715-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="c7715-144">Bu yeoman oluşturucunun seçili geliştirme dilini ve hedef kapsayıcı konak isteyen birkaç soruyla ister.</span><span class="sxs-lookup"><span data-stu-id="c7715-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![yo docker](./media/image21.png)

<span data-ttu-id="c7715-146">Örneğin, Şekil 4-17 Windows ve Mac'te yo çalışmak üzere önceden yapılandırılmış örnek kodu projeleri (şu anda .NET Core, Golang ve desteklenen diller olarak Node.js) oluşturacak docker çalıştıran, her iki durumda da Terminal gelen iki ekran görüntüleri gösterir Docker üstündeki.</span><span class="sxs-lookup"><span data-stu-id="c7715-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="c7715-147">Şekil 4-17: yo docker komut aracını (soldaki) Windows ve Mac'te</span><span class="sxs-lookup"><span data-stu-id="c7715-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="c7715-148">Şekil 4-18 iskele kurulmuş yerinde varolan bir .NET Core projesi oluşturduktan sonra yo docker kullanarak bir örnek sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7715-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="c7715-149">Şekil 4-18: yo docker varolan bir .NET Core ile proje bir yerde</span><span class="sxs-lookup"><span data-stu-id="c7715-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="c7715-150">DockerFile ("microsoft/dotnet:1.0.0-core" kullanarak gibi) kullanacaksınız temel hangi Docker görüntüsü belirtin.</span><span class="sxs-lookup"><span data-stu-id="c7715-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="c7715-151">Genellikle resmi herhangi depodan alabilirsiniz temel bir görüntü üstünde özel görüntünüzü oluşturacaksınız [Docker hub'a kayıt defteri](https://hub.docker.com/) (gibi bir [.NET Core için görüntü](https://hub.docker.com/r/microsoft/dotnet/) veya bir [Node.jsiçin](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="c7715-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="c7715-152">***Seçenek A: kullanımı var olan bir resmi Docker görüntüsünü***</span><span class="sxs-lookup"><span data-stu-id="c7715-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="c7715-153">Sürüm numarası olan bir dil yığınının resmi bir depo kullanarak (geliştirme, test ve üretim dahil) tüm makinelerde aynı dil özellikleri kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7715-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="c7715-154">.NET Core kapsayıcı için bir örnek DockerFile aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="c7715-154">Following is a sample DockerFile for a .NET Core container:</span></span>

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="c7715-155">Bu durumda, onu microsoft/aspnetcore:1.0.1 adlı Linux için resmi ASP.NET Core Docker görüntüsünün 1.0.1 sürümü kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="c7715-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="c7715-156">Daha fazla ayrıntı için başvurun [ASP.NET Core Docker görüntüsünün](https://hub.docker.com/r/microsoft/aspnetcore/) ve [.NET Core Docker görüntüsünün](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="c7715-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="c7715-157">Düğüm: 4 gibi başka bir karşılaştırılabilir görüntü ayrıca kullanıyor-Node.js veya diğer önceden yapılandırılmış birçok görüntüleri kullanılabilir geliştirme diller için onbuild [Docker hub'a](https://hub.docker.com/explore/).</span><span class="sxs-lookup"><span data-stu-id="c7715-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="c7715-158">DockerFile içinde de (örneğin, bağlantı noktası 80) çalışma zamanında kullanacağı TCP bağlantı noktasını dinlemek için Docker istemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="c7715-159">Uygulamayı çalıştırmak nasıl Docker bilmesi için kullanmakta olduğunuz dil/framework bağlı olarak DockerFile ekleyebilirsiniz yapılandırmasının diğer satırlar vardır.</span><span class="sxs-lookup"><span data-stu-id="c7715-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="c7715-160">ENTRYPOINT satırıyla örneği için ihtiyacınız \["dotnet", "MyCustomMicroservice.dll"\] oluşturup, hizmetinizi çalıştırmak için bir yaklaşım bağlı olarak birden çok çeşitleri sahip olabilirsiniz, ancak bir .NET Core uygulamayı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="c7715-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="c7715-161">Derleme ve çalıştırma .NET uygulaması için SDK ve dotnet CLI kullanıyorsanız, biraz farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="c7715-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="c7715-162">ENTRYPOINT satır yanı sıra ek satırlar, uygulamanız için seçtiğiniz dil/platforma bağlı olarak farklı olacaktır alt çizgidir.</span><span class="sxs-lookup"><span data-stu-id="c7715-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="c7715-163">**Daha fazla bilgi** .NET Core uygulamaları için Docker görüntülerinizi oluşturmak hakkında daha fazla bilgi için Git <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="c7715-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="c7715-164">Kendi görüntüleri oluşturma hakkında daha fazla bilgi için şuraya gidin [ https://docs.docker.com/engine/\öğreticileri/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span><span class="sxs-lookup"><span data-stu-id="c7715-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="c7715-165">**Birden çok platform görüntüsü depoları**</span><span class="sxs-lookup"><span data-stu-id="c7715-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="c7715-166">Windows kapsayıcıları daha yaygın hale gibi tek bir depo Linux ve Windows görüntüsü gibi platform çeşitleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c7715-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="c7715-167">Bu, birden çok platformu gibi karşılamak üzere tek bir depoyu kullanacak şekilde satıcılar için mümkün kılar Docker gelen yeni bir özelliktir [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) DockerHub kayıt kullanılabilir deposu.</span><span class="sxs-lookup"><span data-stu-id="c7715-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="c7715-168">Özellik Canlı geldiğinde aynı görüntü adı Linux ana bilgisayardan çekme Linux değişken çeker ancak bu görüntüyü Windows ana bilgisayardan çekme Windows değişken çeker.</span><span class="sxs-lookup"><span data-stu-id="c7715-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="c7715-169">***Temel görüntünüzde sıfırdan seçenek B: oluşturma***</span><span class="sxs-lookup"><span data-stu-id="c7715-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="c7715-170">Bu konuda açıklandığı gibi sıfırdan kendi Docker temel görüntü oluşturabilir [makale](https://docs.docker.com/engine/userguide/eng-image/baseimages/) Docker gelen.</span><span class="sxs-lookup"><span data-stu-id="c7715-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="c7715-171">Bu Docker ile yeni başlıyorsanız, sizin için en iyi şekilde büyük olasılıkla bir senaryodur, ancak temel görüntünüzün belirli BITS ayarlamak istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7715-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="c7715-172">3. adım: özel Docker görüntülerinizi hizmetinizi katıştırmak oluşturma</span><span class="sxs-lookup"><span data-stu-id="c7715-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="c7715-173">Uygulamanızı oluşur her özel hizmeti için ilgili görüntü oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="c7715-174">Uygulamanızı bir tek hizmeti veya web uygulaması oluşuyorsa, yalnızca tek bir görüntü gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="c7715-175">Görüntüleri genel ortamında oluşturulmayacak bir Git deposu (sürekli tümleştirme), kaynak kodunuzu itme her "dış döngü DevOps iş akışı" dikkate alarak, görüntüleri otomatik derleme süreci tarafından oluşturulur, Kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="c7715-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="c7715-176">Ancak Biz bu dış döngü rota gitmeyi göz önünde bulundurun önce kaynak denetim sistemi (Git, vb.) düzgün çalışmayabilir kod itme yok böylece Docker uygulama gerçekte düzgün çalıştığından emin olmak gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="c7715-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="c7715-177">Bu nedenle, her geliştirici, yerel olarak test ve bunlar tam bir özelliği bildirme veya kaynak denetim sistemi değiştirmek istediğiniz kadar geliştirmeye devam etmek için tüm iç döngüsü işlemi yapmak öncelikle gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="c7715-178">Yerel ortamınıza ve DockerFile kullanarak bir görüntü oluşturmak için docker yapı komutu, Şekil 4-19'gösterildiği gibi kullanabilirsiniz (de çalıştırabilirsiniz docker compose'u birkaç kapsayıcıları/Hizmetleri tarafından oluşturulmuş uygulamalar için yukarı--yapı).</span><span class="sxs-lookup"><span data-stu-id="c7715-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="c7715-179">Şekil 4-19: çalışan docker derleme</span><span class="sxs-lookup"><span data-stu-id="c7715-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="c7715-180">İsteğe bağlı olarak, doğrudan docker çalıştırmak yerine projenin klasöründen derleme, ilk çalıştırma dotnet kullanarak komut yayımlamak ve docker yapı çalıştırmak gerekli .NET kitaplıklarıyla dağıtılabilir bir klasör oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7715-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="c7715-181">Bu örnekte, bu bir Docker görüntü cesardl/netcore-webapı-mikro adı ile oluşturur-docker: ilk (: önce belirli bir sürümü gibi bir etiketi olan).</span><span class="sxs-lookup"><span data-stu-id="c7715-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="c7715-182">Bu adım birkaç kapsayıcıları ile oluşan Docker uygulamanızı oluşturmak için gereken her özel görüntü için alabilir.</span><span class="sxs-lookup"><span data-stu-id="c7715-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="c7715-183">Var olan görüntüleri, yerel depoda (geliştirme makinenizi) docker kullanarak görüntüleri komutu, Şekil 4-20'de gösterildiği gibi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7715-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="c7715-184">Şekil 4-20: docker görüntüleri kullanarak var olan görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c7715-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="c7715-185">4. adım: (İsteğe bağlı) tanımlama docker-compose.yml birden çok hizmetleriyle oluşan bir Docker uygulaması oluştururken, hizmetleri</span><span class="sxs-lookup"><span data-stu-id="c7715-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="c7715-186">Docker-compose.yml dosyası ile oluşturulmuş bir uygulama olarak bir sonraki adım bölümde açıklanan dağıtım komutlarla dağıtılması için ilgili hizmetler kümesini tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c7715-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="c7715-187">Bu, ana dosyasında veya kök çözüm klasör oluşturmanız gerekir. Aşağıdaki docker-compose.yml dosyası benzer içeriğe sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="c7715-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

```yml
version: '2'
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

<span data-ttu-id="c7715-188">Bu örnekte, bu dosya, iki hizmet tanımlar: web hizmeti (özel hizmeti) ve redis hizmeti (popüler önbellek hizmeti).</span><span class="sxs-lookup"><span data-stu-id="c7715-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="c7715-189">Somut bir Docker görüntü her biri için kullanılacak ihtiyacımız şekilde her bir hizmet bir kapsayıcı olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="c7715-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="c7715-190">Bu belirli web hizmeti için görüntü aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="c7715-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="c7715-191">DockerFile geçerli dizinde gelen derleme</span><span class="sxs-lookup"><span data-stu-id="c7715-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="c7715-192">Kullanıma sunulan bağlantı noktası 80 konak makinedeki 81 numaralı bağlantı noktasına kapsayıcısı üzerinde ilet</span><span class="sxs-lookup"><span data-stu-id="c7715-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="c7715-193">Konaktaki görüntüsünü yeniden oluşturmak zorunda kalmadan kodu değiştirmeniz edinerek kapsayıcı içindeki /code için proje bağlama</span><span class="sxs-lookup"><span data-stu-id="c7715-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="c7715-194">Web hizmeti redis hizmetine bağlama</span><span class="sxs-lookup"><span data-stu-id="c7715-194">Link the web service to the redis service</span></span>

<span data-ttu-id="c7715-195">Redis hizmet kullandığı [son ortak redis görüntü](https://hub.docker.com/_/redis/) Docker hub'a kayıt defterinden çekilen.</span><span class="sxs-lookup"><span data-stu-id="c7715-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="c7715-196">[redis](https://redis.io/) sunucu tarafı uygulamalar için çok popüler önbellek sistemidir.</span><span class="sxs-lookup"><span data-stu-id="c7715-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="c7715-197">5. adım: Derleme ve Docker uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="c7715-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="c7715-198">Yalnızca tek bir kapsayıcı uygulamanız varsa, yalnızca, Docker ana (VM veya fiziksel sunucu) dağıtarak çalıştırmak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="c7715-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="c7715-199">Uygulamanız birden çok hizmetlerini yapılırsa, ancak yapmanız *onu oluşturan*, çok.</span><span class="sxs-lookup"><span data-stu-id="c7715-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="c7715-200">Farklı seçenekler görelim.</span><span class="sxs-lookup"><span data-stu-id="c7715-200">Let's see the different options.</span></span>

<span data-ttu-id="c7715-201">***Y: Çalıştır tek bir kapsayıcı veya hizmet seçeneği***</span><span class="sxs-lookup"><span data-stu-id="c7715-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="c7715-202">Aşağıda gösterildiği gibi komutu çalıştırmak docker kullanarak Docker görüntünün çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c7715-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="c7715-203">Bu belirli dağıtım için biz 5000 iç bağlantı noktası 80 numaralı bağlantı noktasına gönderilen istekleri yönlendirme olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c7715-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="c7715-204">Şimdi, uygulama dış ana bilgisayar düzeyinde 80 numaralı bağlantı noktasında dinliyor.</span><span class="sxs-lookup"><span data-stu-id="c7715-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="c7715-205">***Seçenek B: oluşturma ve çalıştırma birden çok kapsayıcı uygulama***</span><span class="sxs-lookup"><span data-stu-id="c7715-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="c7715-206">Çoğu Kurumsal senaryoda, Docker uygulama birden çok hizmetlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="c7715-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="c7715-207">Bu durumlarda, komutunu çalıştırabilirsiniz docker compose'u (Şekil 4-21 yukarı), hangi daha önce oluşturmuş olabileceğiniz docker-compose.yml dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7715-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="c7715-208">Bu komutu çalıştırmak, tüm ilgili kapsayıcılarında oluşan bir uygulamayla dağıtır.</span><span class="sxs-lookup"><span data-stu-id="c7715-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="c7715-209">Şekil 4-21: "docker-oluşturmanıza" komutunu çalıştırarak sonuçları</span><span class="sxs-lookup"><span data-stu-id="c7715-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="c7715-210">Docker çalıştırdıktan sonra-oluşturmanıza, uygulamanızı ve ilgili kaldırıldığından, Docker ana bilgisayara VM gösterimi Şekil 4-22'de gösterildiği gibi dağıttığınız.</span><span class="sxs-lookup"><span data-stu-id="c7715-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="c7715-211">Şekil 4-22: VM ile dağıtılan Docker kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="c7715-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="c7715-212">Not docker-oluşturan ayarlama ve çalıştırma docker kapsayıcılarınızı geliştirme ortamında test etmek için yeterli olabilir, ancak, bunları hiç Docker kümeleriyle çalışmak beklediğiniz ve Docker Swarm, Mesosphere DC/OS veya Kubernetes orchestrators gibi kullanamayabilir ölçeği oluşturabilmek.</span><span class="sxs-lookup"><span data-stu-id="c7715-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="c7715-213">Gibi bir küme kullanıyorsanız [Docker Swarm modu](https://docs.docker.com/engine/swarm/) dağıtmak ve docker hizmet oluşturmak için tek Hizmetleri gibi ya da bunu olduğunuzda ek komutları ile test gerek (Docker için Windows ve Mac sürümünden itibaren kullanılabilir sürüm 1.12), birkaç kapsayıcıları için oluşan bir uygulama dağıtımı, paket oluşturma docker kullanarak ve docker makalesinde açıklandığı gibi bir yığın oluşturulmuş uygulama dağıtarak myBundleFile, dağıtma [dağıtılmış uygulama paketleri](https://blog.docker.com/2016/06/docker-app-bundle/) Docker gelen.</span><span class="sxs-lookup"><span data-stu-id="c7715-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="c7715-214">İçin [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) ve [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) farklı dağıtım komutlarını ve komut dosyaları da kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c7715-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="c7715-215">6. adım: Docker uygulamanızda (yerel olarak yerel CD VM) Test</span><span class="sxs-lookup"><span data-stu-id="c7715-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="c7715-216">Bu adımı uygulamanız yapılması bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="c7715-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="c7715-217">Bir çok basit .NET Core Web API'si "Merhaba tek kapsayıcısı veya hizmet dağıtılan World", yalnızca DockerFile belirtilen TCP bağlantı noktası sağlayarak hizmete erişmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="c7715-218">Localhost üzerinde hizmetinize gitmek için açık değilse IP adresi makine için bu komutu kullanarak bulun:</span><span class="sxs-lookup"><span data-stu-id="c7715-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="c7715-219">docker Makine IP *kapsayıcı adı bilgisayarınızı*</span><span class="sxs-lookup"><span data-stu-id="c7715-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="c7715-220">Docker ana bilgisayarında, bir tarayıcı açın ve o siteye gidin; Şekil 4-23'te gösterildiği gibi çalışır, uygulama/hizmet görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7715-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="c7715-221">Şekil 4-23: localhost kullanarak yerel olarak Docker uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="c7715-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="c7715-222">Nasıl bunu çalıştırmak, docker ile daha önce açıklandığı gibi dağıtılmış olduğu için 80 numaralı bağlantı noktasını kullanıyor, ancak dahili olarak, bağlantı noktası 5000 yönlendirildi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c7715-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="c7715-223">Bu terminal durumundan CURL kullanarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7715-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="c7715-224">Windows Docker yüklemede varsayılan IP 10.0.75.1, Şekil 4-24'de gösterilen aynıdır.</span><span class="sxs-lookup"><span data-stu-id="c7715-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="c7715-225">Şekil 4-24: CURL kullanarak yerel olarak Docker uygulamayı test etme</span><span class="sxs-lookup"><span data-stu-id="c7715-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="c7715-226">**Docker üzerinde çalışan bir kapsayıcı hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="c7715-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="c7715-227">Node.js ve .NET Core kapsayıcıları gibi diğer platformlarda kullanıyorsanız, visual Studio Code hata ayıklama Docker destekler.</span><span class="sxs-lookup"><span data-stu-id="c7715-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="c7715-228">Ayrıca Docker .NET Core kapsayıcılarında Visual Studio kullanırken bir sonraki bölümde açıklandığı gibi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7715-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="c7715-229">**Daha fazla bilgi:** Node.js Docker kapsayıcılarında hata ayıklama hakkında daha fazla bilgi için şuraya gidin <https://blog.docker.com/2016/07/live-debugging-docker/> ve [ https://blogs.msdn.microsoft.com/\ kullanıcı\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-Big-Debugging-Updates-Rich-Object-hover-Conditional-Breakpoints-node-js-Mono-More/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span><span class="sxs-lookup"><span data-stu-id="c7715-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c7715-230">[Önceki] (docker-apps-development-environment.md) [sonraki] (visual-studio-araçları-için-docker.md)</span><span class="sxs-lookup"><span data-stu-id="c7715-230">[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)</span></span>

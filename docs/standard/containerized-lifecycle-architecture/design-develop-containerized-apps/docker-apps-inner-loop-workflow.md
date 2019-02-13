---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamaları geliştirmek için "İç döngü" iş akışı öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 03eb4662e55551678105fa9ef25b42cc05c132a5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219094"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="d4aa9-103">Docker uygulamaları için iç döngü geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="d4aa9-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="d4aa9-104">Tüm DevOps kapsayan dış döngü iş akışı tetiklemeden önce döngüsü, tüm uygulama kodlama, kullanıcılarınızın tercih edilen diller veya platformlar ve yerel olarak test her geliştiricinin makine üzerinde (Şekil 4-14) başlar.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="d4aa9-105">Ancak her durumda çok önemli bir nokta ortak hangi dil, çerçeve veya platformlar, seçtiğiniz ne olursa olsun gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="d4aa9-106">Bu belirli bir iş akışında, her zaman geliştirdiğiniz ve Docker kapsayıcıları, ancak yerel olarak test etme.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="d4aa9-107">Şekil 4-14: İç döngü geliştirme bağlamı</span><span class="sxs-lookup"><span data-stu-id="d4aa9-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="d4aa9-108">Bu bileşenler kapsayıcı veya bir Docker görüntüsü örneğini içerir:</span><span class="sxs-lookup"><span data-stu-id="d4aa9-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="d4aa9-109">Bir işletim sistemi seçimi (örneğin, bir Linux dağıtımı veya Windows)</span><span class="sxs-lookup"><span data-stu-id="d4aa9-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="d4aa9-110">Geliştirici (örneğin, uygulama ikili değerleri) tarafından eklenen dosyaları</span><span class="sxs-lookup"><span data-stu-id="d4aa9-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="d4aa9-111">(Örneğin, ortam ayarlarını ve bağımlılıklarını) yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d4aa9-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="d4aa9-112">Docker ile çalıştırmak için hangi işlemleri için yönergeler</span><span class="sxs-lookup"><span data-stu-id="d4aa9-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="d4aa9-113">(Sonraki bölümde açıklanmıştır) işlem olarak Docker kullanan iç döngü geliştirme iş akışı ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="d4aa9-114">Bu yalnızca bir kez yapmanız gerektiğinden ortamı ayarlamak için ilk adımlarında olmadığını dahil dikkate alın.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="d4aa9-115">Visual Studio Code ve Docker CLI'yı kullanarak bir Docker kapsayıcısı içinde tek bir uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4aa9-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="d4aa9-116">Uygulamaları, kendi Hizmetleri artı ek kitaplıklar (bağımlılıklar) oluşur.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="d4aa9-117">Şekil 4-15, genellikle her adımın ayrıntılı açıklamaları tarafından izlenen bir Docker uygulaması derlerken, gerçekleştirmesi gereken temel adımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="d4aa9-118">Şekil 4-15: Docker CLI'yı kullanarak kapsayıcılı Docker uygulamaları için yaşam döngüsü için üst düzey iş akışı</span><span class="sxs-lookup"><span data-stu-id="d4aa9-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="d4aa9-119">1. Adım: Visual Studio Code'da kodlamaya başlayın ve ilk uygulama/hizmet temel oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4aa9-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="d4aa9-120">Uygulamanızı geliştirdiğiniz biçimini, Docker yaptığınız gibi oldukça benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="d4aa9-121">Geliştirmeye devam ederken, dağıtan ve uygulamanızı veya yerel ortamınızda (örneğin, bir Linux VM veya Windows) yerleştirilen Docker kapsayıcıları içinde çalışan hizmetleri test etme, farktır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="d4aa9-122">**Yerel ortamınızda ayarlama**</span><span class="sxs-lookup"><span data-stu-id="d4aa9-122">**Setting up your local environment**</span></span>

<span data-ttu-id="d4aa9-123">Mac ve Windows için Docker'ın en son sürümleri, Docker uygulamaları geliştirmek için hiç olmadığı kadar kolay ve kurulumu basittir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="d4aa9-124">**Daha fazla bilgi** için Docker Windows ayarlama hakkında yönergeler için Git [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="d4aa9-125">Mac için Docker ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="d4aa9-126">Ayrıca, Docker CLI'yı kullanırken uygulamanızı aslında geliştirebilmeniz bir kod düzenleyicisi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="d4aa9-127">Microsoft, Mac, Windows ve Linux üzerinde desteklenir ve IntelliSense ile sağlayan bir basit Kod Düzenleyicisi Visual Studio Code sağlar [birçok dil için destek](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python ve çoğu Modern dilleri) [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), [Git tümleştirmesiyle](https://code.visualstudio.com/Docs/editor/versioncontrol) ve [uzantıları desteğiyle](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="d4aa9-128">Bu düzenleyici Mac ve Linux geliştiriciler için harika bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="d4aa9-129">Windows tam Visual Studio uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="d4aa9-130">**Daha fazla bilgi** Visual Studio için Windows, Mac veya Linux yükleme ile ilgili yönergeler için Git <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>

<span data-ttu-id="d4aa9-131">Docker CLI ile çalışır ve herhangi bir kod Düzenleyicisi'ni kullanarak kodunuzu yazın, ancak Visual Studio Code kullanıyorsanız, bunu Dockerfile yazar için kolay ve docker-compose.yml dosyaları çalışma alanınızda kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="d4aa9-132">Ayrıca, altında Docker CLI'yı kullanarak ayrıntılandırılmış işlemleri çalışması gereken betikleri ister IDE üzerinden Visual Studio Code görevler çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="d4aa9-133">Visual Studio Code'u yüklemek için ihtiyacınız uzantı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="d4aa9-134">Bunu tuşuna Ctrl + Shift + P yapmak için yazın **ext yükleme**, ve Uzantıları'nı çalıştırın: Market uzantısı listesini getirmek için komut uzantısı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="d4aa9-135">Sonra aşağıdakileri yazın **docker** sonuçları filtreleyin ve ardından Dockerfile ve Docker Compose dosyası (yml) destek uzantısı, Şekil 4-16 gösterildiği şekilde seçin.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="d4aa9-136">Şekil 4-16: Visual Studio Code'da Docker uzantısını yükleme</span><span class="sxs-lookup"><span data-stu-id="d4aa9-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="d4aa9-137">2. Adım: Mevcut bir görüntüyü (düz işletim sistemi veya geliştirme ortamları .NET Core, Node.js ve Ruby gibi) ilgili bir DockerFile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4aa9-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="d4aa9-138">Kapsayıcısını, dağıtılmasını ve oluşturulacak özel görüntü başına bir DockerFile gerekir, bu nedenle, uygulamanız tek bir özel hizmet yapılırsa, tek bir DockerFile gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="d4aa9-139">Ancak, uygulamanız birden çok hizmeti (olduğu gibi bir mikro hizmetler mimarisinde) oluşan, hizmet başına bir Dockerfile gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="d4aa9-140">DockerFile, uygulamanızı veya hizmetinizi kök klasörü içinde genellikle yerleştirilir ve Docker nasıl ayarlanacağını ve söz konusu uygulamayı veya hizmeti çalıştırılacağını bilmesi gereken komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="d4aa9-141">DockerFile'ı oluşturabilir ve kodunuzun yanı sıra projenize ekleyin (node.js, .NET Core, vb.), veya ortama yeni başladıysanız, aşağıdaki ipucu göz atın.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="d4aa9-142">Adlı bir komut satırı aracını kullanabilirsiniz [yo docker](https://github.com/Microsoft/generator-docker), iskele oluşturulduğunu hangi dosyaların projenizden dili seçin ve gerekli Docker yapılandırma dosyaları ekler.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="d4aa9-143">Temelde, kullanmaya başlayan geliştiriciler yardımcı olmak için ilgili DockerFile oluşturduğu docker-compose.yml ve ilişkili diğer komut oluşturun ve Docker kapsayıcılarınızı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="d4aa9-144">Bu yeoman oluşturucuyu birkaç soruyu soran seçili geliştirme dil ve hedef kapsayıcı konağı, ister.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![yo docker](./media/image21.png)

<span data-ttu-id="d4aa9-146">Örneğin, Şekil 4-17 Windows ve Mac'te yo çalışmak üzere önceden yapılandırılmış örnek kod projeleri (şu anda .NET Core, Golang ve desteklenen dilleri olarak Node.js) oluşturacak docker, çalıştırma, her iki durumda da iki ekran görüntüleri terminaller gösterir Docker'ın üstünde.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="d4aa9-147">Şekil 4-17: yo docker komut aracını (solda) Windows ve Mac'te</span><span class="sxs-lookup"><span data-stu-id="d4aa9-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="d4aa9-148">Şekil 4-18 iskelesi oluşturulmuş için var olan bir .NET Core projesi oluşturduktan sonra yo docker kullanan bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="d4aa9-149">Şekil 4-18: yo docker ile var olan bir .NET Core proje bir yerde</span><span class="sxs-lookup"><span data-stu-id="d4aa9-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="d4aa9-150">DockerFile ("microsoft/dotnet:1.0.0-core" kullanma gibi) kullanacaksınız hangi temel Docker görüntüsünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="d4aa9-151">Özel görüntünüzü herhangi bir resmi deponun sayfasından edinebilirsiniz bir temel görüntünün üstüne genellikle oluşturacağınız [Docker Hub kayıt defterinde](https://hub.docker.com/) (gibi bir [.NET Core için görüntü](https://hub.docker.com/r/microsoft/dotnet/) veya bir [Node.jsiçin](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="d4aa9-152">***Seçenek A: Var olan resmi bir Docker görüntüsü kullanma***</span><span class="sxs-lookup"><span data-stu-id="d4aa9-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="d4aa9-153">Bir sürüm numarasına sahip bir resmi bir dil yığını depoyu kullanarak, aynı dil özellikleri (geliştirme, test ve üretim dahil) tüm makinelerde kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="d4aa9-154">DockerFile'bir .NET Core kapsayıcı için bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d4aa9-154">Following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="d4aa9-155">Bu durumda, bunu microsoft/aspnetcore:1.0.1 adlı Linux için resmi ASP.NET Core Docker görüntüsünü 1.0.1 sürümü kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="d4aa9-156">Daha fazla ayrıntı için başvurun [ASP.NET Core Docker görüntüsünün](https://hub.docker.com/r/microsoft/aspnetcore/) ve [.NET Core Docker görüntüsünün](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="d4aa9-157">Düğüm: 4 gibi başka bir karşılaştırılabilir görüntü kullanabilecek-Node.js veya diğer önceden yapılandırılmış birçok görüntüler bulabileceğiniz geliştirme diller için onbuıld [Docker Hub](https://hub.docker.com/explore/).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="d4aa9-158">DockerFile içinde ayrıca isteyin (örneğin, bağlantı noktası 80) çalışma zamanında kullanacağınız TCP bağlantı noktasını dinlemek için Docker gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="d4aa9-159">Docker, uygulamayı çalıştırmak nasıl olduğunu bilmesi için kullanmakta olduğunuz dil/framework bağlı olarak DockerFile içinde ekleyebilirsiniz yapılandırmanın diğer satırlar var.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="d4aa9-160">ENTRYPOINT satırla örneği için ihtiyacınız \["dotnet", "MyCustomMicroservice.dll"\] oluşturup hizmetinizi çalıştırmak için bir yaklaşım bağlı olarak birden çok çeşitleri olabilir ancak bir .NET Core uygulamasını çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="d4aa9-161">.NET uygulaması derleyebilir ve için SDK'sı ve dotnet CLI kullanıyorsanız, biraz farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="d4aa9-162">ENTRYPOINT satırı artı ek satırlar, uygulamanız için seçtiğiniz dil/platforma bağlı olarak farklı olacaktır alt çizgidir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="d4aa9-163">**Daha fazla bilgi** .NET Core uygulamaları için Docker görüntüleri oluşturma hakkında daha fazla bilgi için Git <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="d4aa9-164">Kendi görüntülerinizi oluşturma hakkında daha fazla bilgi edinmek için Git [ https://docs.docker.com/engine/\ öğreticiler/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="d4aa9-165">**Çok platformlu görüntü depolar**</span><span class="sxs-lookup"><span data-stu-id="d4aa9-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="d4aa9-166">Windows kapsayıcıları daha yaygın hale geldikçe, tek bir depoda bir Linux ve Windows görüntüsü gibi platformu çeşitleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="d4aa9-167">Bu, tek bir depo gibi birden çok platform karşılamak üzere kullanılacak satıcılar için mümkün kılan docker'da kullanıma sunulacak yeni bir özelliktir [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) DockerHub kayıt defterinde kullanılabilir olan depo.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="d4aa9-168">Bir özellik Canlı gelir gibi görüntü adının aynısını, bir Linux ana bilgisayarından alınan Linux değişken çeker ise Windows konaktan bu görüntüyü çekmeyi Windows değişken çeker.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="d4aa9-169">***Seçenek B: Temel görüntünüzü sıfırdan oluşturma***</span><span class="sxs-lookup"><span data-stu-id="d4aa9-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="d4aa9-170">Bu konuda açıklandığı gibi sıfırdan kendi Docker temel görüntüsünde oluşturabilirsiniz [makale](https://docs.docker.com/engine/userguide/eng-image/baseimages/) docker.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="d4aa9-171">Bu, Docker ile yeni başlıyorsanız, sizin için en büyük olasılıkla bir senaryodur ancak kendi temel görüntü belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="d4aa9-172">3. Adım: Hizmetinizi katıştırarak, özel Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d4aa9-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="d4aa9-173">Uygulamanızı oluşturan özel her hizmet için ilgili bir görüntü oluşturmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="d4aa9-174">Tek bir hizmeti veya web uygulaması, uygulamanızı oluşuyorsa, yalnızca tek bir görüntü gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="d4aa9-175">Görüntüler genel bir ortamda oluşturulur böylece, kaynak kodunuzda bir Git deposuna (sürekli tümleştirme) gönderdiğinizde "dış döngü DevOps iş akışı" dikkate alarak, görüntüleri bir otomatik yapı işlemi tarafından gelen oluşturulur, Kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="d4aa9-176">Ancak Biz bu dış döngü rota giderek göz önünde bulundurun önce kaynak denetim sistemine (Git, vb.) düzgün çalışmayabilir kod itme yoktur, böylece Docker uygulaması aslında düzgün çalıştığından emin olmak gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="d4aa9-177">Bu nedenle, her geliştirici, yerel olarak test etmek ve tam bir özelliği bildirme veya kaynak denetim sistemine değiştirmek istedikleri kadar geliştirmeye devam etmek için tüm iç döngü işlem yapmak öncelikle gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="d4aa9-178">Yerel ortamınıza ve DockerFile'ı kullanarak bir görüntü oluşturmak için docker oluşturma komutu, Şekil 4-19'gösterildiği gibi kullanabilirsiniz (da çalıştırabilirsiniz docker-compose--'kurmak birkaç kapsayıcılar/Hizmetleri tarafından oluşturulan uygulamalar için derleme).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="d4aa9-179">Şekil 4-19: Çalışan docker derleme</span><span class="sxs-lookup"><span data-stu-id="d4aa9-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="d4aa9-180">İsteğe bağlı olarak, doğrudan docker çalıştırmak yerine Proje klasöründen yapı, ilk çalıştırma dotnet kullanarak yayımlama komutu ve docker derleme çalıştırın gerekli .NET kitaplıklarıyla dağıtılabilir bir klasör oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="d4aa9-181">Bu örnekte, bu bir Docker görüntüsü cesardl/netcore-webapı-mikro adı ile oluşturur-docker: ilk (: önce belirli bir sürümü gibi bir etiketi olan).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="d4aa9-182">Bu adım birkaç kapsayıcılar ile oluşturulmuş Docker uygulamanızı oluşturmak için ihtiyacınız olan her bir özel görüntüsünün alabilir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="d4aa9-183">Var olan görüntülerden yerel deponuzda (geliştirme makinenize) docker'ı kullanarak görüntü komutu, Şekil 4-20'de gösterildiği gibi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="d4aa9-184">Şekil 4-20: Docker görüntüleri kullanarak var olan görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d4aa9-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="d4aa9-185">4. Adım: (İsteğe bağlı) Birden çok hizmeti ile oluşturulmuş bir Docker uygulaması derlerken, hizmetlerinizi docker-compose.yml tanımlayın</span><span class="sxs-lookup"><span data-stu-id="d4aa9-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="d4aa9-186">Docker-compose.yml dosyasıyla, bir dizi adım bir sonraki bölümde açıklanan dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili hizmetler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="d4aa9-187">Bu ana dosyasında veya kök Çözüm klasörü oluşturmanız gerekir; Aşağıdaki docker-compose.yml dosyasına benzer içeriğe sahip olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="d4aa9-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

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

<span data-ttu-id="d4aa9-188">Bu durumda, bu dosya, iki hizmet tanımlar: web hizmeti (özel hizmeti) ve redis hizmetinin (popüler önbellek hizmeti).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="d4aa9-189">Yüzden somut bir Docker görüntüsü her biri için kullanılacak her bir hizmet bir kapsayıcı olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="d4aa9-190">Bu belirli bir web hizmeti için görüntüyü şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="d4aa9-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="d4aa9-191">DockerFile geçerli dizinde yapıdan</span><span class="sxs-lookup"><span data-stu-id="d4aa9-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="d4aa9-192">Konak makinedeki 81 numaralı bağlantı noktasına kapsayıcı üzerindeki 80 kullanıma sunulan bağlantı noktası iletme</span><span class="sxs-lookup"><span data-stu-id="d4aa9-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="d4aa9-193">Proje dizini görüntüsünü yeniden oluşturmak zorunda kalmadan kodu değiştirmeniz edinerek /code kapsayıcı içindeki konağa üzerinde bağlama</span><span class="sxs-lookup"><span data-stu-id="d4aa9-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="d4aa9-194">Redis hizmetine web hizmetine bağlama</span><span class="sxs-lookup"><span data-stu-id="d4aa9-194">Link the web service to the redis service</span></span>

<span data-ttu-id="d4aa9-195">Redis hizmeti kullandığı [en son genel redis görüntüsünü](https://hub.docker.com/_/redis/) Docker Hub kayıt defterinden çekilir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="d4aa9-196">[redis](https://redis.io/) sunucu tarafı uygulamalar için çok popüler önbellek sistemidir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="d4aa9-197">5. Adım: Derleme ve Docker uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d4aa9-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="d4aa9-198">Yalnızca tek bir kapsayıcı uygulamanız varsa, Docker Konağı (VM veya fiziksel sunucu) dağıtarak çalıştırmak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="d4aa9-199">Uygulamanızı birden çok hizmetlerini yapılırsa, ancak yapmanız *onu oluşturan*, çok.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="d4aa9-200">Farklı seçenekler görelim.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-200">Let's see the different options.</span></span>

<span data-ttu-id="d4aa9-201">***Seçenek A: Tek kapsayıcı ya da hizmet çalıştırma***</span><span class="sxs-lookup"><span data-stu-id="d4aa9-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="d4aa9-202">Burada gösterildiği gibi komutu çalıştırın: docker kullanarak Docker görüntüsünü çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d4aa9-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="d4aa9-203">Bu belirli dağıtım için biz 5000 iç bağlantı noktası için 80 numaralı bağlantı noktasına gönderilen istekleri yönlendirme, unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="d4aa9-204">Artık, uygulamanın dış konak düzeyinde 80 numaralı bağlantı noktasında dinliyor.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="d4aa9-205">***Seçenek B: Oluşturma ve birden çok kapsayıcılı bir uygulama çalıştırma***</span><span class="sxs-lookup"><span data-stu-id="d4aa9-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="d4aa9-206">Çoğu Kurumsal senaryolarda, Docker uygulaması birden çok hizmetlerini oluşacaktır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="d4aa9-207">Bu durumlarda komutunu çalıştırabilirsiniz docker-compose (Şekil 4-21 ayarlama), hangi daha önce oluşturmuş olabileceğiniz docker-compose.yml dosyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="d4aa9-208">Bu komutu çalıştırarak tüm ilgili kapsayıcılarında oluşan bir uygulama dağıtır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="d4aa9-209">Şekil 4-21: "Docker compose up" komutunu çalıştırma sonuçları</span><span class="sxs-lookup"><span data-stu-id="d4aa9-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="d4aa9-210">Docker'ı çalıştırdıktan sonra-oluşturmanıza, uygulamanız ve onun ilişkili kapsayıcılar, Docker konağı VM gösteriminde Şekil 4-22'de gösterildiği gibi dağıtın.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="d4aa9-211">Şekil 4-22: Dağıtılmış Docker kapsayıcıları ile VM</span><span class="sxs-lookup"><span data-stu-id="d4aa9-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="d4aa9-212">Not docker-compose ayarlama ve docker run kapsayıcılarınızı geliştirme ortamınızda test etmek için yeterli olmayabilir. ancak, bunları Docker kümeleriyle çalışmak görmeyi ve Docker Swarm, Mesosphere DC/OS veya Kubernetes düzenleyicileri gibi kullanmamak ölçeği artırma oluşturabilmek.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="d4aa9-213">Gibi bir küme kullanıyorsanız [Docker Swarm modu](https://docs.docker.com/engine/swarm/) (Docker için Windows ve Mac sürümünden itibaren kullanılabilir sürüm 1.12), dağıtın ve docker hizmeti oluşturmak için tek Hizmetleri gibi ya da işiniz ek komutlar ile test için ihtiyacınız birden çok kapsayıcılardan oluşan bir uygulama dağıtma, paket oluşturma kullanarak docker ve docker dağıtma myBundleFile, makalesinde açıklandığı gibi bir yığın oluşturulmuş uygulama dağıtarak [dağıtılmış uygulama paketleri](https://blog.docker.com/2016/06/docker-app-bundle/) docker.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="d4aa9-214">İçin [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) ve [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) farklı dağıtım komutları ve komut dosyaları, de kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="d4aa9-215">6. Adım: (Yerel olarak, yerel CD sanal makinenizin) Docker uygulamanızı test edin</span><span class="sxs-lookup"><span data-stu-id="d4aa9-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="d4aa9-216">Bu adım, uygulamanızı yapmak bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="d4aa9-217">Bir çok basit .NET Core Web API'si "Hello tek kapsayıcı veya hizmet olarak dağıtılan World", yalnızca Dockerfile'da belirtilen TCP bağlantı noktası sağlayarak hizmete erişmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="d4aa9-218">Localhost, hizmetinize gidin açık değilse şu komutu kullanarak makine için IP adresini bulun:</span><span class="sxs-lookup"><span data-stu-id="d4aa9-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="d4aa9-219">docker-machine IP *your-container-name*</span><span class="sxs-lookup"><span data-stu-id="d4aa9-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="d4aa9-220">Docker konağı, bir tarayıcı açın ve o siteye gidin; Şekil 4-23'te gösterildiği gibi uygulama/hizmet çalışıyorsa, görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="d4aa9-221">Şekil 4-23: Docker uygulamanızı yerel olarak localhost kullanarak test etme</span><span class="sxs-lookup"><span data-stu-id="d4aa9-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="d4aa9-222">Nasıl bunu çalıştırmak, docker ile daha önce açıklandığı gibi dağıtılmış olduğu için 80 numaralı bağlantı noktasını kullanıyor, ancak dahili olarak, bağlantı noktası 5000 yönlendirilen unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="d4aa9-223">Bu terminalde CURL kullanarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="d4aa9-224">Windows üzerindeki Docker yüklemede varsayılan IP 10.0.75.1, Şekil 4-24 gösterilen aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="d4aa9-225">Şekil 4-24: Docker uygulaması'nın CURL kullanarak yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="d4aa9-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="d4aa9-226">**Docker üzerinde çalışan bir kapsayıcısında hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="d4aa9-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="d4aa9-227">Node.js ve .NET Core kapsayıcıları gibi diğer platformlarda kullanıyorsanız, visual Studio Code hata ayıklama Docker destekler.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="d4aa9-228">Ayrıca Docker kapsayıcılarında .NET Core Visual Studio kullanarak, sonraki bölümde açıklandığı gibi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4aa9-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="d4aa9-229">**Daha fazla bilgi:** Node.js Docker kapsayıcılarında hata ayıklama hakkında daha fazla bilgi için şuraya gidin <https://blog.docker.com/2016/07/live-debugging-docker/> ve [ https://blogs.msdn.microsoft.com/\ kullanıcı\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-Big-Debugging-Updates-Rich-Object-hover-Conditional-Breakpoints-node-js-Mono-More/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span><span class="sxs-lookup"><span data-stu-id="d4aa9-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="d4aa9-230">[Önceki](docker-apps-development-environment.md)
>[İleri](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="d4aa9-230">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
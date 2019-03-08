---
title: Docker uygulamaları için iç döngü geliştirme iş akışı
description: Docker uygulamaları geliştirmek için "İç döngü" iş akışı öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1ed0feeec682f5a79bc38db6a101b751ea4dbc3a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676674"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="87a12-103">Docker uygulamaları için iç döngü geliştirme iş akışı</span><span class="sxs-lookup"><span data-stu-id="87a12-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="87a12-104">Tüm DevOps kapsayan dış döngü iş akışı tetiklemeden önce döngüsü, tüm uygulama kodlama, kullanıcılarınızın tercih edilen diller veya platformlar ve yerel olarak test her geliştiricinin makine üzerinde (Şekil 4-21) başlar.</span><span class="sxs-lookup"><span data-stu-id="87a12-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="87a12-105">Ancak her durumda, önemli bir nokta ortak hangi dil, çerçeve veya platformlar, seçtiğiniz ne olursa olsun sahip olacaksınız.</span><span class="sxs-lookup"><span data-stu-id="87a12-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="87a12-106">Bu belirli bir iş akışında, her zaman geliştirirken ve Docker kapsayıcıları, ancak yerel olarak test etme.</span><span class="sxs-lookup"><span data-stu-id="87a12-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Adım 1 - kod/Çalıştır/Hata Ayıkla](./media/image18.png)

<span data-ttu-id="87a12-108">**Şekil 4-21**.</span><span class="sxs-lookup"><span data-stu-id="87a12-108">**Figure 4-21**.</span></span> <span data-ttu-id="87a12-109">İç döngü geliştirme bağlamı</span><span class="sxs-lookup"><span data-stu-id="87a12-109">Inner-loop development context</span></span>

<span data-ttu-id="87a12-110">Bu bileşenler kapsayıcı veya bir Docker görüntüsü örneğini içerir:</span><span class="sxs-lookup"><span data-stu-id="87a12-110">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="87a12-111">Bir işletim sistemi seçimi (örneğin, bir Linux dağıtımı veya Windows)</span><span class="sxs-lookup"><span data-stu-id="87a12-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="87a12-112">Geliştirici (örneğin, uygulama ikili değerleri) tarafından eklenen dosyaları</span><span class="sxs-lookup"><span data-stu-id="87a12-112">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="87a12-113">(Örneğin, ortam ayarlarını ve bağımlılıklarını) yapılandırma</span><span class="sxs-lookup"><span data-stu-id="87a12-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="87a12-114">Docker ile çalıştırmak için hangi işlemleri için yönergeler</span><span class="sxs-lookup"><span data-stu-id="87a12-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="87a12-115">(Sonraki bölümde açıklanmıştır) işlem olarak Docker kullanan iç döngü geliştirme iş akışı ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="87a12-116">Yalnızca bir kez yapmanız gerektiğinden ortamı ayarlamak için ilk adımları dahil olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="87a12-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="87a12-117">Visual Studio Code ve Docker CLI'yı kullanarak bir Docker kapsayıcısı içinde tek bir uygulama oluşturma</span><span class="sxs-lookup"><span data-stu-id="87a12-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="87a12-118">Uygulamaları, kendi Hizmetleri artı ek kitaplıklar (bağımlılıklar) oluşur.</span><span class="sxs-lookup"><span data-stu-id="87a12-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="87a12-119">Şekil 4-22, genellikle her adımın ayrıntılı açıklamaları tarafından izlenen bir Docker uygulaması derlerken, gerçekleştirmesi gereken temel adımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="87a12-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![İş akışı genel bakış: Adım 1 - kod, 2. adım - dockerfile'ları, 3. adım - yazma dockerfile'ları ile 4. adımda tanımlanan görüntüleri oluşturma - 5. adım - Çalıştır kapsayıcıları docker-compose dosya ile hizmetleri tanımlamak veya dış döngü (CI/CD işlem hatları) başlayamaz veya de devam etmek için oluşturulan uygulamalar, adım 6 - Test uygulamaları, 7. adım - gönderin veloping.](./media/image19.png)

<span data-ttu-id="87a12-121">**Şekil 4-22**.</span><span class="sxs-lookup"><span data-stu-id="87a12-121">**Figure 4-22**.</span></span> <span data-ttu-id="87a12-122">Docker CLI'yı kullanarak kapsayıcılı Docker uygulamaları için yaşam döngüsü için üst düzey iş akışı</span><span class="sxs-lookup"><span data-stu-id="87a12-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="87a12-123">1. Adım: Visual Studio Code'da kodlamaya başlayın ve ilk uygulama/hizmet temel oluşturma</span><span class="sxs-lookup"><span data-stu-id="87a12-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="87a12-124">Uygulamanızı geliştirdiğiniz yolu Docker yaptığınız gibi benzer.</span><span class="sxs-lookup"><span data-stu-id="87a12-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="87a12-125">Geliştirmeye devam ederken, dağıtma ve uygulama veya yerel ortamınızda (örneğin, bir Linux VM veya Windows) yerleştirilen Docker kapsayıcıları içinde çalışan hizmetleri test etme, farktır.</span><span class="sxs-lookup"><span data-stu-id="87a12-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="87a12-126">**Yerel ortamınızda ayarlama**</span><span class="sxs-lookup"><span data-stu-id="87a12-126">**Setting up your local environment**</span></span>

<span data-ttu-id="87a12-127">Mac ve Windows için Docker'ın en son sürümleri, Docker uygulamaları geliştirmek için hiç olmadığı kadar kolay ve kurulumu basittir.</span><span class="sxs-lookup"><span data-stu-id="87a12-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [! BİLGİLERİ]
>
> <span data-ttu-id="87a12-129">Docker için Windows ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="87a12-129">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="87a12-130">Mac için Docker ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="87a12-130">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="87a12-131">Ayrıca, Docker CLI'yı kullanırken uygulamanızı aslında geliştirebilmeniz bir kod düzenleyicisi gerekir.</span><span class="sxs-lookup"><span data-stu-id="87a12-131">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="87a12-132">Microsoft, Mac, Windows ve Linux üzerinde desteklenir ve IntelliSense ile sağlayan bir basit Kod Düzenleyicisi Visual Studio Code sağlar [birçok dil için destek](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python ve çoğu Modern dilleri) [hata ayıklama](https://code.visualstudio.com/Docs/editor/debugging), [Git tümleştirmesiyle](https://code.visualstudio.com/Docs/editor/versioncontrol) ve [uzantıları desteğiyle](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="87a12-132">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="87a12-133">Bu düzenleyici Mac ve Linux geliştiriciler için harika bir çözümdür.</span><span class="sxs-lookup"><span data-stu-id="87a12-133">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="87a12-134">Windows tam Visual Studio uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-134">In Windows, you also can use the full Visual Studio application.</span></span>

> [! BİLGİLERİ]
>
> <span data-ttu-id="87a12-136">Visual Studio Code için Windows, Mac veya Linux yükleme ile ilgili yönergeler için Git <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="87a12-136">For instructions on installing Visual Studio Code for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="87a12-137">Mac için Docker ayarlama hakkında yönergeler için Git <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="87a12-137">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="87a12-138">Docker CLI ile çalışır ve herhangi bir kod Düzenleyicisi'ni kullanarak kodunuzu yazın, ancak Visual Studio Code ile Docker uzantısını kullanarak kolaylaştırır Yazar `Dockerfile` ve `docker-compose.yml` çalışma alanınızdaki dosyaları.</span><span class="sxs-lookup"><span data-stu-id="87a12-138">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="87a12-139">Visual Studio IDE'den kod altında Docker CLI'yı kullanarak Docker komutları yürütmek için görevleri ve betikler çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-139">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="87a12-140">VS Code için Docker uzantısını aşağıdaki özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="87a12-140">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="87a12-141">Otomatik `Dockerfile` ve `docker-compose.yml` dosya oluşturma</span><span class="sxs-lookup"><span data-stu-id="87a12-141">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="87a12-142">Söz dizimi vurgulama ve vurgulu ipuçları `docker-compose.yml` ve `Dockerfile` dosyaları</span><span class="sxs-lookup"><span data-stu-id="87a12-142">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="87a12-143">(Tamamlamalar) için IntelliSense `Dockerfile` ve `docker-compose.yml` dosyaları</span><span class="sxs-lookup"><span data-stu-id="87a12-143">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="87a12-144">Linting (hatalar ve uyarılar) için `Dockerfile` dosyaları</span><span class="sxs-lookup"><span data-stu-id="87a12-144">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="87a12-145">En yaygın Docker komutları için komut paleti (F1) Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="87a12-145">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="87a12-146">Görüntüleri ve kapsayıcılar yönetmek için Gezgini tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="87a12-146">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="87a12-147">DockerHub ve Azure kapsayıcı kayıt defterleri görüntülerinden Azure App Service'e dağıtma</span><span class="sxs-lookup"><span data-stu-id="87a12-147">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="87a12-148">Docker uzantısını yüklemek için Ctrl + Shift + P tuşlarına basın yazın `ext install`, ve ardından Market uzantısı listesini getirmek için uzantı yükleme komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="87a12-148">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="87a12-149">Sonra aşağıdakileri yazın **docker** sonuçları filtrelemek ve ardından, Şekil 4-23'te gösterildiği gibi Docker desteği uzantısı seçin.</span><span class="sxs-lookup"><span data-stu-id="87a12-149">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![VS Code için Docker uzantısını görünümü.](./media/image20.png)

<span data-ttu-id="87a12-151">**Şekil 4-23**.</span><span class="sxs-lookup"><span data-stu-id="87a12-151">**Figure 4-23**.</span></span> <span data-ttu-id="87a12-152">Visual Studio Code'da Docker uzantısını yükleme</span><span class="sxs-lookup"><span data-stu-id="87a12-152">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="87a12-153">2. Adım: Mevcut bir görüntüyü (düz işletim sistemi veya geliştirme ortamları .NET Core, Node.js ve Ruby gibi) ilgili bir DockerFile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="87a12-153">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="87a12-154">İhtiyacınız olacak bir `DockerFile` ve dağıtılması için kapsayıcı başına oluşturulacak özel görüntü.</span><span class="sxs-lookup"><span data-stu-id="87a12-154">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="87a12-155">Uygulamanızı tek bir özel hizmet yapılırsa, tek bir gerekir `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="87a12-155">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="87a12-156">Ancak uygulamanız birden çok hizmetlerinin (olduğu gibi bir mikro hizmetler mimarisinde) oluşuyorsa, tane gerekecektir `Dockerfile` hizmet başına.</span><span class="sxs-lookup"><span data-stu-id="87a12-156">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="87a12-157">`DockerFile` Uygulamanızı veya hizmetinizi kök klasöründe bulunan yaygın olarak yerleştirilir ve Docker nasıl ayarlanacağını ve söz konusu uygulamayı veya hizmeti çalıştırılacağını bilmesi gereken komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="87a12-157">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="87a12-158">Oluşturabileceğiniz, `DockerFile` ve kodunuzu birlikte projenize ekleyin (node.js, .NET Core, vb.), veya ortama yeni başladıysanız, aşağıdaki ipucu göz atın.</span><span class="sxs-lookup"><span data-stu-id="87a12-158">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
>
> <span data-ttu-id="87a12-159">Docker uzantısını kullanırken yol göstermesi için kullanabileceğiniz `Dockerfile` ve `docker-compose.yml` Docker kapsayıcıları için ilgili dosyaları.</span><span class="sxs-lookup"><span data-stu-id="87a12-159">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="87a12-160">Sonuç olarak, bu tür dosyaları bu aracı olmadan büyük olasılıkla yazacaksınız, ancak Docker uzantısını kullanmaktır, öğrenme eğrisi hızlandıracaktır iyi bir başlangıç noktası.</span><span class="sxs-lookup"><span data-stu-id="87a12-160">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="87a12-161">Şekil 4-24'te bir docker nasıl görebilirsiniz-compose dosyası, VS Code için Docker uzantısını kullanarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="87a12-161">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![VS Code için Docker uzantısını konsol görünümü.](./media/image24.png)

<span data-ttu-id="87a12-163">**Şekil 4-24**.</span><span class="sxs-lookup"><span data-stu-id="87a12-163">**Figure 4-24**.</span></span> <span data-ttu-id="87a12-164">Docker dosyaları kullanılarak eklenen **çalışma komut Docker ekleme dosyaları**</span><span class="sxs-lookup"><span data-stu-id="87a12-164">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="87a12-165">Bir DockerFile eklediğinizde, kullanıyor hangi temel Docker görüntüsüne belirtin (kullanma gibi `FROM microsoft/aspnetcore`).</span><span class="sxs-lookup"><span data-stu-id="87a12-165">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM microsoft/aspnetcore`).</span></span> <span data-ttu-id="87a12-166">Özel görüntünüzü herhangi bir resmi deponun aldığınız bir temel görüntünün üstüne genellikle oluşturacaksınız [Docker Hub kayıt defterinde](https://hub.docker.com/) (gibi bir [.NET Core için görüntü](https://hub.docker.com/r/microsoft/dotnet/) veya [Node.jsiçin](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="87a12-166">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="87a12-167">***Var olan resmi bir Docker görüntüsü kullanma***</span><span class="sxs-lookup"><span data-stu-id="87a12-167">***Use an existing official Docker image***</span></span>

<span data-ttu-id="87a12-168">Bir sürüm numarasına sahip bir resmi bir dil yığını depoyu kullanarak, aynı dil özellikleri (geliştirme, test ve üretim dahil) tüm makinelerde kullanılabilir olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="87a12-168">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="87a12-169">DockerFile'bir .NET Core kapsayıcı için bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="87a12-169">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
# Base Docker image to use  
FROM microsoft/dotnet:2.1-aspnetcore-runtime
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="87a12-170">Bu durumda, görüntü resmi ASP.NET Core Docker görüntü (Linux ve Windows için çok arch), satır başına 2.1 sürümünü dayalı `FROM microsoft/dotnet:2.1-aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="87a12-170">In this case, the image is based on version 2.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM microsoft/dotnet:2.1-aspnetcore-runtime`.</span></span> <span data-ttu-id="87a12-171">(Bu konu hakkında daha fazla bilgi için bkz. [ASP.NET Core, Docker görüntüsü](https://hub.docker.com/r/microsoft/aspnetcore/) sayfası ve [.NET Core, Docker görüntüsü](https://hub.docker.com/r/microsoft/dotnet/) sayfası).</span><span class="sxs-lookup"><span data-stu-id="87a12-171">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page).</span></span>

<span data-ttu-id="87a12-172">DockerFile içinde Docker çalışma zamanında (örneğin, bağlantı noktası 80) kullanan TCP bağlantı noktası dinleyecek şekilde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-172">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="87a12-173">Dil ve çerçeve kullanmakta olduğunuz bağlı olarak bir Dockerfile içinde ek yapılandırma ayarları belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-173">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="87a12-174">Örneğin, `ENTRYPOINT` ile satır `["dotnet", "MySingleContainerWebApp.dll"]` .NET Core uygulamasını çalıştırmak için Docker söyler.</span><span class="sxs-lookup"><span data-stu-id="87a12-174">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="87a12-175">SDK ve .NET Core CLI'yı kullanıyorsanız (`dotnet CLI`) .NET uygulaması derleme ve çalıştırma için bu ayarı farklı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="87a12-175">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="87a12-176">Burada temel nokta ENTRYPOINT satır ve diğer ayarları uygulamanız için seçtiğiniz dil ve platform bağımlı olduğunu ' dir.</span><span class="sxs-lookup"><span data-stu-id="87a12-176">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [! BİLGİLERİ]
>
> <span data-ttu-id="87a12-178">.NET Core uygulamaları için Docker görüntüleri oluşturma hakkında daha fazla bilgi için Git <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="87a12-178">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="87a12-179">Kendi görüntülerinizi oluşturma hakkında daha fazla bilgi edinmek için Git <https://docs.docker.com/engine/tutorials/dockerimages/>.</span><span class="sxs-lookup"><span data-stu-id="87a12-179">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="87a12-180">**Çok yay görüntü depolar**</span><span class="sxs-lookup"><span data-stu-id="87a12-180">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="87a12-181">Bir tek bir görüntü adı bir depoda bir Linux görüntüsü ve bir Windows görüntüsünü gibi platformu çeşitleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="87a12-181">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="87a12-182">Bu özellik, birden çok Platformu (diğer bir deyişle, Linux ve Windows) karşılamak için tek bir depo oluşturmak Microsoft (temel Görüntü Oluşturucu) gibi satıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="87a12-182">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="87a12-183">Örneğin, [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) Docker Hub kayıt defterinde depo, görüntü adının aynısını kullanarak Linux ve Windows Nano sunucu için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="87a12-183">For example, the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="87a12-184">Çekme [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) görüntüyü Windows konaktan, görüntü adının aynısını, bir Linux ana bilgisayarından alınan Linux değişken çeker ise Windows değişken çeker.</span><span class="sxs-lookup"><span data-stu-id="87a12-184">Pulling the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="87a12-185">***Temel görüntünüzü sıfırdan oluşturma***</span><span class="sxs-lookup"><span data-stu-id="87a12-185">***Create your base image from scratch***</span></span>

<span data-ttu-id="87a12-186">Bu konuda açıklandığı gibi sıfırdan kendi Docker temel görüntüsünde oluşturabilirsiniz [makale](https://docs.docker.com/engine/userguide/eng-image/baseimages/) docker.</span><span class="sxs-lookup"><span data-stu-id="87a12-186">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="87a12-187">Bu senaryo sizin için en iyi Docker ile yeni başlıyor ister, ancak kendi temel görüntü belirli bitlerini ayarlamak istiyorsanız, bunu yapabilirsiniz, büyük olasılıkla değil.</span><span class="sxs-lookup"><span data-stu-id="87a12-187">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="87a12-188">3. Adım: Hizmetinizi katıştırarak, özel Docker görüntüleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="87a12-188">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="87a12-189">Uygulamanızı oluşturan özel her hizmet için ilgili bir görüntü oluşturmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="87a12-189">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="87a12-190">Tek bir hizmeti veya web uygulaması, uygulamanızı oluşuyorsa, yalnızca tek bir görüntü gerekir.</span><span class="sxs-lookup"><span data-stu-id="87a12-190">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
>
> <span data-ttu-id="87a12-191">Görüntüler genel bir ortamda oluşturulur böylece, kaynak kodunuzu Git deposuna (sürekli tümleştirme) öğesinden gönderdiğinizde "dış döngü DevOps iş akışı" dikkate alarak, görüntüleri bir otomatik yapı işlemi tarafından oluşturulur, Kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="87a12-191">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="87a12-192">Ancak Biz bu dış döngü rota giderek düşünmeden önce kaynak denetim sistemine (Git, vb.) düzgün çalışmayabilir kod itme yoktur, böylece Docker uygulaması aslında düzgün çalıştığından emin olmak oluşturmamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87a12-192">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="87a12-193">Bu nedenle, her geliştirici, yerel olarak test etmek ve tam bir özelliği bildirme veya kaynak denetim sistemine değiştirmek istedikleri kadar geliştirmeye devam etmek için tüm iç döngü işlem yapmak öncelikle gerekir.</span><span class="sxs-lookup"><span data-stu-id="87a12-193">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="87a12-194">Yerel ortamınıza ve DockerFile'ı kullanarak bir görüntü oluşturmak için docker oluşturma komutu, Şekil 4-25 gösterildiği gibi kullanabilirsiniz (da çalıştırabilirsiniz `docker-compose up --build` birkaç kapsayıcılar/Hizmetleri tarafından oluşturulan uygulamalar için).</span><span class="sxs-lookup"><span data-stu-id="87a12-194">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![İlerleme durumunu indirme görüntüleri gösteren docker-compose derleme, konsol çıktısı.](./media/image25.png)

<span data-ttu-id="87a12-196">**Şekil 4-25**.</span><span class="sxs-lookup"><span data-stu-id="87a12-196">**Figure 4-25**.</span></span> <span data-ttu-id="87a12-197">Çalışan docker derleme</span><span class="sxs-lookup"><span data-stu-id="87a12-197">Running docker build</span></span>

<span data-ttu-id="87a12-198">İsteğe bağlı olarak, doğrudan çalıştırmak yerine `docker build` proje klasöründen, ilk dağıtılabilir bir klasör Çalıştır'ı kullanarak gerekli .NET kitaplıkları oluşturabilirsiniz `dotnet publish` komutunu ve ardından çalıştırın `docker build`.</span><span class="sxs-lookup"><span data-stu-id="87a12-198">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="87a12-199">Bu örnek adıyla bir Docker görüntüsü oluşturur `cesardl/netcore-webapi-microservice-docker:first` (`:first` belirli bir sürümü gibi bir etiket).</span><span class="sxs-lookup"><span data-stu-id="87a12-199">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="87a12-200">Bu adım birkaç kapsayıcılar ile oluşturulmuş Docker uygulamanızı oluşturmak için ihtiyacınız olan her bir özel görüntüsünün alabilir.</span><span class="sxs-lookup"><span data-stu-id="87a12-200">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="87a12-201">Var olan görüntülerden yerel deponuzda (geliştirme makinenize) docker'ı kullanarak görüntü komutu, Şekil 4-26 gösterildiği şekilde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-201">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Konsol, var olan görüntülerden gösteren komut docker görüntülerinden çıktısı.](./media/image26.png)

<span data-ttu-id="87a12-203">**Şekil 4-26**.</span><span class="sxs-lookup"><span data-stu-id="87a12-203">**Figure 4-26**.</span></span> <span data-ttu-id="87a12-204">Docker görüntüleri kullanarak var olan görüntüleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="87a12-204">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="87a12-205">4. Adım: Birden çok hizmeti ile oluşturulmuş bir Docker uygulaması derlerken, hizmetlerinizi docker-compose.yml tanımlayın</span><span class="sxs-lookup"><span data-stu-id="87a12-205">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="87a12-206">İle `docker-compose.yml` dosyası, bir dizi adım bir sonraki bölümde açıklanan dağıtım komutları ile oluşturulmuş bir uygulama olarak dağıtılması için ilgili hizmetler tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-206">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="87a12-207">Bu ana dosyasında veya kök Çözüm klasörü oluşturmak; benzer şekilde, bu konuda gösterilen içeriği olması gereken `docker-compose.yml` dosyası:</span><span class="sxs-lookup"><span data-stu-id="87a12-207">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

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

<span data-ttu-id="87a12-208">Bu durumda, bu dosya, iki hizmet tanımlar: web hizmeti (özel hizmeti) ve redis hizmetinin (popüler önbellek hizmeti).</span><span class="sxs-lookup"><span data-stu-id="87a12-208">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="87a12-209">Yüzden somut bir Docker görüntüsü her biri için kullanılacak her bir hizmet bir kapsayıcı olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="87a12-209">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="87a12-210">Bu belirli bir web hizmeti için görüntüyü şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="87a12-210">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="87a12-211">DockerFile geçerli dizinde yapıdan</span><span class="sxs-lookup"><span data-stu-id="87a12-211">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="87a12-212">Konak makinedeki 81 numaralı bağlantı noktasına kapsayıcı üzerindeki 80 kullanıma sunulan bağlantı noktası iletme</span><span class="sxs-lookup"><span data-stu-id="87a12-212">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="87a12-213">Proje dizini görüntüsünü yeniden oluşturmak zorunda kalmadan kodu değiştirmeniz edinerek /code kapsayıcı içindeki konağa üzerinde bağlama</span><span class="sxs-lookup"><span data-stu-id="87a12-213">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="87a12-214">Redis hizmetine web hizmetine bağlama</span><span class="sxs-lookup"><span data-stu-id="87a12-214">Link the web service to the redis service</span></span>

<span data-ttu-id="87a12-215">Redis hizmeti kullandığı [en son genel redis görüntüsünü](https://hub.docker.com/_/redis/) Docker Hub kayıt defterinden çekilir.</span><span class="sxs-lookup"><span data-stu-id="87a12-215">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="87a12-216">[redis](https://redis.io/) sunucu tarafı uygulamalar için yaygın olarak kullanılan önbellek sistemidir.</span><span class="sxs-lookup"><span data-stu-id="87a12-216">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="87a12-217">5. Adım: Derleme ve Docker uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="87a12-217">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="87a12-218">Yalnızca tek bir kapsayıcı uygulamanız varsa, Docker Konağı (VM veya fiziksel sunucu) dağıtarak çalıştırmak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="87a12-218">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="87a12-219">Uygulamanızı birden çok hizmetlerini yapılırsa, ancak yapmanız *onu oluşturan*, çok.</span><span class="sxs-lookup"><span data-stu-id="87a12-219">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="87a12-220">Farklı seçenekler görelim.</span><span class="sxs-lookup"><span data-stu-id="87a12-220">Let's see the different options.</span></span>

<span data-ttu-id="87a12-221">***Seçenek A: Tek kapsayıcı ya da hizmet çalıştırma***</span><span class="sxs-lookup"><span data-stu-id="87a12-221">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="87a12-222">Burada gösterildiği gibi komutu çalıştırın: docker kullanarak Docker görüntüsünü çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87a12-222">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="87a12-223">Bu belirli dağıtım için biz 5000 iç bağlantı noktası için 80 numaralı bağlantı noktasına gönderilen istekleri yönlendirme.</span><span class="sxs-lookup"><span data-stu-id="87a12-223">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="87a12-224">Şimdi uygulamayı dış konak düzeyinde 80 numaralı bağlantı noktasında dinliyor.</span><span class="sxs-lookup"><span data-stu-id="87a12-224">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="87a12-225">***Seçenek B: Oluşturma ve birden çok kapsayıcılı bir uygulama çalıştırma***</span><span class="sxs-lookup"><span data-stu-id="87a12-225">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="87a12-226">Çoğu Kurumsal senaryolarda, Docker uygulaması birden çok hizmetlerini oluşacaktır.</span><span class="sxs-lookup"><span data-stu-id="87a12-226">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="87a12-227">Bu durumlarda çalıştırabileceğiniz `docker-compose up` daha önce oluşturmuş olabileceğiniz docker-compose.yml dosyasını kullanır (Şekil 4-27), komutu.</span><span class="sxs-lookup"><span data-stu-id="87a12-227">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="87a12-228">Bu komutu çalıştırarak tüm ilgili kapsayıcılarında oluşan bir uygulama dağıtır.</span><span class="sxs-lookup"><span data-stu-id="87a12-228">Running this command deploys a composed application with all of its related containers.</span></span>

![Konsol çıktısı docker-compose komutu.](./media/image27.png)

<span data-ttu-id="87a12-230">**Şekil 4-27**.</span><span class="sxs-lookup"><span data-stu-id="87a12-230">**Figure 4-27**.</span></span> <span data-ttu-id="87a12-231">"Docker compose up" komutunu çalıştırma sonuçları</span><span class="sxs-lookup"><span data-stu-id="87a12-231">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="87a12-232">Çalıştırdıktan sonra `docker-compose up`, uygulamanız ve onun ilişkili kapsayıcılar, Docker konağı VM gösteriminde Şekil 4-28'de gösterildiği gibi dağıttığınız.</span><span class="sxs-lookup"><span data-stu-id="87a12-232">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Çok kapsayıcılı uygulamalar çalıştıran VM.](./media/image28.png)

<span data-ttu-id="87a12-234">**Şekil 4-28**.</span><span class="sxs-lookup"><span data-stu-id="87a12-234">**Figure 4-28**.</span></span> <span data-ttu-id="87a12-235">Dağıtılmış Docker kapsayıcıları ile VM</span><span class="sxs-lookup"><span data-stu-id="87a12-235">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="87a12-236">6. Adım: (Yerel olarak, yerel CD sanal makinenizin) Docker uygulamanızı test edin</span><span class="sxs-lookup"><span data-stu-id="87a12-236">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="87a12-237">Bu adım, uygulamanızı yapmak bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="87a12-237">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="87a12-238">Bir basit'de .NET Core Web API'si "Hello tek kapsayıcı veya hizmet olarak dağıtılan World", yalnızca Dockerfile'da belirtilen TCP bağlantı noktası sağlayarak hizmete erişmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="87a12-238">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="87a12-239">Localhost, hizmetinize gidin açık değilse şu komutu kullanarak makine için IP adresini bulun:</span><span class="sxs-lookup"><span data-stu-id="87a12-239">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="87a12-240">Docker konağı, bir tarayıcı açın ve o siteye gidin; Şekil 4-29 gösterildiği gibi uygulama/hizmet çalışıyorsa, görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="87a12-240">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![API/localhost/değerleri yanıt tarayıcı görünümü.](./media/image29.png)

<span data-ttu-id="87a12-242">**Şekil 4-29**.</span><span class="sxs-lookup"><span data-stu-id="87a12-242">**Figure 4-29**.</span></span> <span data-ttu-id="87a12-243">Docker uygulamanızı yerel olarak localhost kullanarak test etme</span><span class="sxs-lookup"><span data-stu-id="87a12-243">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="87a12-244">80 numaralı bağlantı noktasını kullanıyor, ancak bağlantı noktası 5000 dahili olarak yönlendiriliyor nasıl ile dağıtıldığı olduğu için Not `docker run`, daha önce açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="87a12-244">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="87a12-245">Bu terminalde CURL kullanarak test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-245">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="87a12-246">Windows üzerindeki Docker yüklemede varsayılan IP 10.0.75.1, Şekil 4-30 gösterilen aynıdır.</span><span class="sxs-lookup"><span data-stu-id="87a12-246">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Konsol çıktısı geçmesini http://10.0.75.1/API/values curl ile](./media/image30.png)

<span data-ttu-id="87a12-248">**Şekil 4-30**.</span><span class="sxs-lookup"><span data-stu-id="87a12-248">**Figure 4-30**.</span></span> <span data-ttu-id="87a12-249">Docker uygulaması'nın CURL kullanarak yerel olarak test etme</span><span class="sxs-lookup"><span data-stu-id="87a12-249">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="87a12-250">**Docker üzerinde çalışan bir kapsayıcısında hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="87a12-250">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="87a12-251">Node.js ve .NET Core kapsayıcıları gibi diğer platformlarda kullanıyorsanız, visual Studio Code hata ayıklama Docker destekler.</span><span class="sxs-lookup"><span data-stu-id="87a12-251">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="87a12-252">Ayrıca .NET Core veya .NET Framework Docker kapsayıcılarında kullanırken Windows için Visual Studio veya Mac, sonraki bölümde açıklandığı gibi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87a12-252">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [! BİLGİLERİ]
>
> <span data-ttu-id="87a12-254">Node.js Docker kapsayıcılarında hata ayıklama hakkında daha fazla bilgi için şuraya gidin <https://blog.docker.com/2016/07/live-debugging-docker/> ve <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span><span class="sxs-lookup"><span data-stu-id="87a12-254">To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="87a12-255">[Önceki](docker-apps-development-environment.md)
>[İleri](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="87a12-255">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>

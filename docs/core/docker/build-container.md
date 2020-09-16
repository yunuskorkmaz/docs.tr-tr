---
title: Docker öğreticisi ile uygulama Kapsayıcılı hale getirme
description: Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edineceksiniz.
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: b6775c760ef3f5bf1c9519430b038f149c9cf30f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538507"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="fd831-103">Öğretici: bir .NET Core uygulamasını Kapsayıize edin</span><span class="sxs-lookup"><span data-stu-id="fd831-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="fd831-104">Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="fd831-104">In this tutorial, you'll learn how to containerize a .NET Core application with Docker.</span></span> <span data-ttu-id="fd831-105">Kapsayıcılar, sabit bir altyapı olmak, taşınabilir bir mimari sağlamak ve ölçeklenebilirliği etkinleştirmek gibi birçok özellik ve avantaja sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fd831-105">Containers have many features and benefits, such as being an immutable infrastructure, providing a portable architecture, and enabling scalability.</span></span> <span data-ttu-id="fd831-106">Görüntü, yerel geliştirme ortamınız, özel bulut veya genel bulutunuz için kapsayıcılar oluşturmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd831-106">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="fd831-107">Bu öğreticide şunları yaptınız:</span><span class="sxs-lookup"><span data-stu-id="fd831-107">In this tutorial, you:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="fd831-108">Basit bir .NET Core uygulaması oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="fd831-108">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="fd831-109">.NET Core için Dockerfile oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fd831-109">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="fd831-110">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd831-110">Build a Docker image</span></span>
> - <span data-ttu-id="fd831-111">Docker kapsayıcısı oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="fd831-111">Create and run a Docker container</span></span>

<span data-ttu-id="fd831-112">Docker kapsayıcısının bir .NET Core uygulaması için görevleri oluşturup dağıtduklarını anlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fd831-112">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="fd831-113">*Docker platformu* , uygulamaları *Docker görüntüleri*olarak hızlı bir şekilde oluşturmak ve paketlemek için *Docker altyapısını* kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd831-113">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="fd831-114">Bu görüntüler, katmanlı bir kapsayıcıda dağıtılacak ve çalıştırılacak *Dockerfile* biçiminde yazılır.</span><span class="sxs-lookup"><span data-stu-id="fd831-114">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!NOTE]
> <span data-ttu-id="fd831-115">Bu öğretici ASP.NET Core uygulamalar için **değildir** .</span><span class="sxs-lookup"><span data-stu-id="fd831-115">This tutorial **is not** for ASP.NET Core apps.</span></span> <span data-ttu-id="fd831-116">ASP.NET Core kullanıyorsanız, [bir ASP.NET Core uygulama](/aspnet/core/host-and-deploy/docker/building-net-docker-images) öğreticisini nasıl Kapsayıyoruz hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="fd831-116">If you're using ASP.NET Core, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fd831-117">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="fd831-117">Prerequisites</span></span>

<span data-ttu-id="fd831-118">Aşağıdaki önkoşulları yükler:</span><span class="sxs-lookup"><span data-stu-id="fd831-118">Install the following prerequisites:</span></span>

- <span data-ttu-id="fd831-119">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="fd831-119">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="fd831-120">.NET Core yüklüyse, `dotnet --info` kullanmakta olduğunuz SDK 'yı öğrenmek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd831-120">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>
- [<span data-ttu-id="fd831-121">Docker Community sürümü</span><span class="sxs-lookup"><span data-stu-id="fd831-121">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)
- <span data-ttu-id="fd831-122">*Dockerfile* ve .NET Core örnek uygulaması için geçici çalışma klasörü.</span><span class="sxs-lookup"><span data-stu-id="fd831-122">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="fd831-123">Bu öğreticide, *Docker-Working* adı çalışma klasörü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd831-123">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="fd831-124">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd831-124">Create .NET Core app</span></span>

<span data-ttu-id="fd831-125">Docker kapsayıcısının çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="fd831-125">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="fd831-126">Terminalinizi açın, henüz yapmadıysanız bir çalışma klasörü oluşturun ve bunu girin.</span><span class="sxs-lookup"><span data-stu-id="fd831-126">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="fd831-127">Çalışma klasöründe, *uygulama*adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fd831-127">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

<span data-ttu-id="fd831-128">Klasör ağaclarınız şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="fd831-128">Your folder tree will look like the following:</span></span>

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

<span data-ttu-id="fd831-129">`dotnet new`Komut, *uygulama* adlı yeni bir klasör oluşturur ve bir "Merhaba Dünya" konsol uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd831-129">The `dotnet new` command creates a new folder named *App* and generates a "Hello World" console application.</span></span> <span data-ttu-id="fd831-130">Dizinleri değiştirin ve Terminal oturumunuzda *uygulama* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="fd831-130">Change directories and navigate into the *App* folder, from your terminal session.</span></span> <span data-ttu-id="fd831-131">`dotnet run`Uygulamayı başlatmak için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd831-131">Use the `dotnet run` command to start the app.</span></span> <span data-ttu-id="fd831-132">Uygulama çalışır ve `Hello World!` komutun altına yazdırılır:</span><span class="sxs-lookup"><span data-stu-id="fd831-132">The application will run, and print `Hello World!` below the command:</span></span>

```dotnetcli
dotnet run
Hello World!
```

<span data-ttu-id="fd831-133">Varsayılan şablon, terminale yazdıran bir uygulama oluşturur ve hemen sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fd831-133">The default template creates an app that prints to the terminal and then immediately terminates.</span></span> <span data-ttu-id="fd831-134">Bu öğretici için süresiz olarak döngü yapan bir uygulama kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fd831-134">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="fd831-135">*Program.cs* dosyasını bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="fd831-135">Open the *Program.cs* file in a text editor.</span></span>

> [!TIP]
> <span data-ttu-id="fd831-136">Visual Studio Code kullanıyorsanız, önceki Terminal oturumunda aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="fd831-136">If you're using Visual Studio Code, from the previous terminal session type the following command:</span></span>
>
> ```console
> code .
> ```
>
> <span data-ttu-id="fd831-137">Bu, Visual Studio Code projedeki projeyi içeren *uygulama* klasörünü açar.</span><span class="sxs-lookup"><span data-stu-id="fd831-137">This will open the *App* folder that contains the project in Visual Studio Code.</span></span>

<span data-ttu-id="fd831-138">*Program.cs* aşağıdaki C# kodu gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="fd831-138">The *Program.cs* should look like the following C# code:</span></span>

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="fd831-139">Dosyayı her saniye sayı sayan aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="fd831-139">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

<span data-ttu-id="fd831-140">Dosyayı kaydedin ve ile programı test edin `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="fd831-140">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="fd831-141">Bu uygulamanın süresiz olarak çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fd831-141">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="fd831-142">Durdurmak için <kbd>CTRL + C</kbd> Cancel komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd831-142">Use the cancel command <kbd>Ctrl+C</kbd> to stop it.</span></span> <span data-ttu-id="fd831-143">Aşağıda örnek bir çıktı verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fd831-143">The following is an example output:</span></span>

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="fd831-144">Uygulama için komut satırına bir sayı geçirirseniz, bu miktarı yalnızca bu miktara göre sayılır ve ardından çıkış olur.</span><span class="sxs-lookup"><span data-stu-id="fd831-144">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="fd831-145">`dotnet run -- 5`Beş olarak saymak için deneyin.</span><span class="sxs-lookup"><span data-stu-id="fd831-145">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd831-146">Sonrasında herhangi bir parametre `--` komutuna geçirilmez `dotnet run` ve bunun yerine uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fd831-146">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="fd831-147">.NET Core uygulaması Yayımla</span><span class="sxs-lookup"><span data-stu-id="fd831-147">Publish .NET Core app</span></span>

<span data-ttu-id="fd831-148">.NET Core uygulamasını Docker görüntüsüne eklemeden önce, önce yayımlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fd831-148">Before adding the .NET Core app to the Docker image, first it must be published.</span></span> <span data-ttu-id="fd831-149">Kapsayıcının uygulamanın yayımlanmış sürümünü çalıştırması en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="fd831-149">It is best to have the container run the published version of the app.</span></span> <span data-ttu-id="fd831-150">Uygulamayı yayımlamak için şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fd831-150">To publish the app, run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="fd831-151">Bu komut, uygulamanızı *Yayımla* klasörüne derler.</span><span class="sxs-lookup"><span data-stu-id="fd831-151">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="fd831-152">Çalışma klasöründeki *Yayımla* klasörünün yolu `.\App\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="fd831-152">The path to the *publish* folder from the working folder should be `.\App\bin\Release\netcoreapp3.1\publish\`</span></span>

#### <a name="windows"></a>[<span data-ttu-id="fd831-153">Windows</span><span class="sxs-lookup"><span data-stu-id="fd831-153">Windows</span></span>](#tab/windows)

<span data-ttu-id="fd831-154">*Uygulama* klasöründen, *NetCore.Docker.dll* dosyasının oluşturulduğunu doğrulamak için Yayımla klasörünün bir dizin listesini alın.</span><span class="sxs-lookup"><span data-stu-id="fd831-154">From the *App* folder, get a directory listing of the publish folder to verify that the *NetCore.Docker.dll* file was created.</span></span>

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[<span data-ttu-id="fd831-155">Linux</span><span class="sxs-lookup"><span data-stu-id="fd831-155">Linux</span></span>](#tab/linux)

<span data-ttu-id="fd831-156">`ls`Bir dizin listesi almak için komutunu kullanın ve *NetCore.Docker.dll* dosyasının oluşturulduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="fd831-156">Use the `ls` command to get a directory listing and verify that the *NetCore.Docker.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a><span data-ttu-id="fd831-157">Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd831-157">Create the Dockerfile</span></span>

<span data-ttu-id="fd831-158">*Dockerfile* dosyası `docker build` komut tarafından bir kapsayıcı görüntüsü oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd831-158">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="fd831-159">Bu dosya, uzantısı olmayan *Dockerfile* adlı bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="fd831-159">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="fd831-160">*. Csproj* Içeren dizinde *dockerfile* adlı bir dosya oluşturun ve bunu bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="fd831-160">Create a file named *Dockerfile* in directory containing the *.csproj* and open it in a text editor.</span></span> <span data-ttu-id="fd831-161">Bu öğretici, .NET Core çalışma zamanı görüntüsünü içeren ASP.NET Core çalışma zamanı görüntüsünü kullanır ve .NET Core konsol uygulamasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="fd831-161">This tutorial will use the ASP.NET Core runtime image (which contains the .NET Core runtime image) and corresponds with the .NET Core console application.</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> <span data-ttu-id="fd831-162">ASP.NET Core çalışma zamanı görüntüsü kasıtlı olarak burada kullanılır, ancak `mcr.microsoft.com/dotnet/core/runtime:3.1` görüntü kullanılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd831-162">The ASP.NET Core runtime image is used intentionally here, although the `mcr.microsoft.com/dotnet/core/runtime:3.1` image could have been used.</span></span>

<span data-ttu-id="fd831-163">`FROM`Anahtar sözcüğü tam bir Docker kapsayıcı görüntüsü adı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="fd831-163">The `FROM` keyword requires a fully qualified Docker container image name.</span></span> <span data-ttu-id="fd831-164">Microsoft Container Registry (MCR, mcr.microsoft.com), genel olarak erişilebilen kapsayıcıları barındıran Docker Hub 'ının bir genel yöneticisdir.</span><span class="sxs-lookup"><span data-stu-id="fd831-164">The Microsoft Container Registry (MCR, mcr.microsoft.com) is a syndicate of Docker Hub - which hosts publicly accessible containers.</span></span> <span data-ttu-id="fd831-165">Segment, kapsayıcının `dotnet/core` `aspnet` kapsayıcı görüntüsü adı olduğu yerde kapsayıcı deposudur.</span><span class="sxs-lookup"><span data-stu-id="fd831-165">The `dotnet/core` segment is the container repository, where as the `aspnet` segment is the container image name.</span></span> <span data-ttu-id="fd831-166">Görüntü, `3.1` sürüm oluşturma için kullanılan ile etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="fd831-166">The image is tagged with `3.1`, which is used for versioning.</span></span> <span data-ttu-id="fd831-167">Bu nedenle, `mcr.microsoft.com/dotnet/core/aspnet:3.1` .NET Core 3,1 çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="fd831-167">Thus, `mcr.microsoft.com/dotnet/core/aspnet:3.1` is the .NET Core 3.1 runtime.</span></span> <span data-ttu-id="fd831-168">SDK 'nizin hedeflediği çalışma zamanıyla eşleşen çalışma zamanı sürümünü çekdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="fd831-168">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="fd831-169">Örneğin, önceki bölümde oluşturulan uygulama .NET Core 3,1 SDK 'sını ve *Dockerfile* içinde başvurulan temel görüntüyü **3,1**ile etiketledi.</span><span class="sxs-lookup"><span data-stu-id="fd831-169">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="fd831-170">*Dockerfile* dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fd831-170">Save the *Dockerfile* file.</span></span> <span data-ttu-id="fd831-171">Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="fd831-171">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="fd831-172">Daha derin düzey dosya ve klasörlerden bazıları, makalede yer kazanmak için atlandı:</span><span class="sxs-lookup"><span data-stu-id="fd831-172">Some of the deeper-level files and folders have been omitted to save space in the article:</span></span>

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

<span data-ttu-id="fd831-173">Terminalinizden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fd831-173">From your terminal, run the following command:</span></span>

```console
docker build -t counter-image -f Dockerfile .
```

<span data-ttu-id="fd831-174">Docker, *Dockerfile*dosyasındaki her satırı işleyecek.</span><span class="sxs-lookup"><span data-stu-id="fd831-174">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="fd831-175">`.` `docker build` Komutunda Docker 'ın bir *dockerfile dosyasını*bulmak için geçerli klasörü kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="fd831-175">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="fd831-176">Bu komut, görüntüyü oluşturur ve bu görüntüye işaret eden **Counter-Image** adlı bir yerel depo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd831-176">This command builds the image and creates a local repository named **counter-image** that points to that image.</span></span> <span data-ttu-id="fd831-177">Bu komut tamamlandıktan sonra, `docker images` yüklenen görüntülerin listesini görmek için komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fd831-177">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="fd831-178">İki görüntünün aynı **görüntü kimliği** değerini paylaştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="fd831-178">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="fd831-179">*Dockerfile* 'daki tek komut yeni görüntünün varolan bir görüntüye dayandırdığı için, her iki görüntü arasında değer aynıdır.</span><span class="sxs-lookup"><span data-stu-id="fd831-179">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="fd831-180">*Dockerfile dosyasına*üç komut ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="fd831-180">Let's add three commands to the *Dockerfile*.</span></span> <span data-ttu-id="fd831-181">Her komut, için **Sayaç-görüntü** deposu giriş noktalarını temsil eden son komutla yeni bir görüntü katmanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd831-181">Each command creates a new image layer with the final command representing the **counter-image** repository entry points to.</span></span>

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

<span data-ttu-id="fd831-182">`COPY`Komut, Docker 'a bilgisayarınızdaki belirtilen klasörü kapsayıcıda bir klasöre kopyalamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="fd831-182">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="fd831-183">Bu örnekte, *Publish* klasörü kapsayıcıda *uygulama* adlı bir klasöre kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="fd831-183">In this example, the *publish* folder is copied to a folder named *App* in the container.</span></span>

<span data-ttu-id="fd831-184">`WORKDIR`Komut, kapsayıcının içindeki **geçerli dizini** *uygulama*olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="fd831-184">The `WORKDIR` command changes the **current directory** inside of the container to *App*.</span></span>

<span data-ttu-id="fd831-185">Sonraki komut, `ENTRYPOINT` Docker öğesine kapsayıcıyı yürütülebilir olarak çalışacak şekilde yapılandırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="fd831-185">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="fd831-186">Kapsayıcı başladığında, `ENTRYPOINT` komutu çalışır.</span><span class="sxs-lookup"><span data-stu-id="fd831-186">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="fd831-187">Bu komut sona erdiğinde kapsayıcı otomatik olarak durur.</span><span class="sxs-lookup"><span data-stu-id="fd831-187">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="fd831-188">Terminalinizden `docker build -t counter-image -f Dockerfile .` komutunu çalıştırın ve komut tamamlandığında komutunu çalıştırın `docker images` .</span><span class="sxs-lookup"><span data-stu-id="fd831-188">From your terminal, run `docker build -t counter-image -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

<span data-ttu-id="fd831-189">*Dockerfile* 'daki her komut bir katman oluşturdu ve BIR **görüntü kimliği**oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="fd831-189">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="fd831-190">Son **görüntü kimliği** (sizinki farklı olacak) **cd11c3df9b19** ve bir sonraki adımda bu görüntüye göre bir kapsayıcı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="fd831-190">The final **IMAGE ID** (yours will be different) is **cd11c3df9b19** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="fd831-191">Bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd831-191">Create a container</span></span>

<span data-ttu-id="fd831-192">Artık uygulamanızı içeren bir görüntünüz olduğuna göre, bir kapsayıcı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd831-192">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="fd831-193">Bir kapsayıcıyı iki şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd831-193">You can create a container in two ways.</span></span> <span data-ttu-id="fd831-194">İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fd831-194">First, create a new container that is stopped.</span></span>

```console
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

<span data-ttu-id="fd831-195">`docker create`Yukarıdaki komutu **sayaç görüntüsü** görüntüsünü temel alan bir kapsayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fd831-195">The `docker create` command from above will create a container based on the **counter-image** image.</span></span> <span data-ttu-id="fd831-196">Bu komutun çıktısı, oluşturulan kapsayıcının **KAPSAYıCı kimliğini** (sizinki farklı olacak) gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd831-196">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="fd831-197">*Tüm* kapsayıcıların listesini görmek için `docker ps -a` komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="fd831-197">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a><span data-ttu-id="fd831-198">Kapsayıcıyı yönetme</span><span class="sxs-lookup"><span data-stu-id="fd831-198">Manage the container</span></span>

<span data-ttu-id="fd831-199">Kapsayıcı belirli bir adla oluşturulmuştur `core-counter` , bu ad kapsayıcıyı yönetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd831-199">The container was created with a specific name `core-counter`, this name is used to manage the container.</span></span> <span data-ttu-id="fd831-200">Aşağıdaki örnek, `docker start` kapsayıcıyı başlatmak için komutunu kullanır ve sonra `docker ps` yalnızca çalıştıran kapsayıcıları göstermek için komutunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="fd831-200">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

<span data-ttu-id="fd831-201">Benzer şekilde, `docker stop` komut kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="fd831-201">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="fd831-202">Aşağıdaki örnek, `docker stop` kapsayıcıyı durdurmak için komutunu kullanır ve ardından `docker ps` hiçbir kapsayıcının çalışmadığını göstermek için komutunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="fd831-202">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="fd831-203">Bir kapsayıcıya bağlanma</span><span class="sxs-lookup"><span data-stu-id="fd831-203">Connect to a container</span></span>

<span data-ttu-id="fd831-204">Bir kapsayıcı çalışmaya başladıktan sonra çıktıyı görmek için bu sunucuya bağlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd831-204">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="fd831-205">`docker start`Ve komutlarını kullanarak `docker attach` kapsayıcıyı başlatın ve çıkış akışına göz atın.</span><span class="sxs-lookup"><span data-stu-id="fd831-205">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="fd831-206">Bu örnekte, <kbd>CTRL + C</kbd> tuş vuruşu, çalışan kapsayıcıyı ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd831-206">In this example, the <kbd>Ctrl+C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="fd831-207">Bu tuş vuruşu, aksi belirtilmediği sürece kapsayıcıdaki işlemi sona erdirmek için kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="fd831-207">This keystroke will end the process in the container unless otherwise specified, which would stop the container.</span></span> <span data-ttu-id="fd831-208">`--sig-proxy=false`Parametresi, <kbd>CTRL + C</kbd> 'nin kapsayıcıdaki işlemi durdurmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd831-208">The `--sig-proxy=false` parameter ensures that <kbd>Ctrl+C</kbd> will not stop the process in the container.</span></span>

<span data-ttu-id="fd831-209">Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saymakta olduğunu doğrulamak için yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="fd831-209">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="fd831-210">Kapsayıcı silme</span><span class="sxs-lookup"><span data-stu-id="fd831-210">Delete a container</span></span>

<span data-ttu-id="fd831-211">Bu makalenin amaçları doğrultusunda, kapsayıcıların hiçbir şey yapmadan asılı istememeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="fd831-211">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="fd831-212">Daha önce oluşturduğunuz kapsayıcıyı silin.</span><span class="sxs-lookup"><span data-stu-id="fd831-212">Delete the container you previously created.</span></span> <span data-ttu-id="fd831-213">Kapsayıcı çalışıyorsa durdurun.</span><span class="sxs-lookup"><span data-stu-id="fd831-213">If the container is running, stop it.</span></span>

```console
docker stop core-counter
```

<span data-ttu-id="fd831-214">Aşağıdaki örnekte tüm kapsayıcılar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd831-214">The following example lists all containers.</span></span> <span data-ttu-id="fd831-215">Ardından, `docker rm` kapsayıcıyı silmek için komutunu kullanır ve ardından çalışan kapsayıcılar için ikinci bir kez kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="fd831-215">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="fd831-216">Tek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="fd831-216">Single run</span></span>

<span data-ttu-id="fd831-217">Docker, `docker run` kapsayıcıyı tek bir komut olarak oluşturup çalıştırmak için komutunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd831-217">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="fd831-218">Bu komut, ve daha sonra çalıştırma gereksinimini ortadan kaldırır `docker create` `docker start` .</span><span class="sxs-lookup"><span data-stu-id="fd831-218">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="fd831-219">Kapsayıcı durdurulduğunda kapsayıcıyı otomatik olarak silmek için de bu komutu ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd831-219">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="fd831-220">Örneğin, `docker run -it --rm` ilk olarak iki şey yapmak için kullanın, kapsayıcıya bağlanmak için otomatik olarak geçerli terminali kullanın ve ardından kapsayıcı tamamlandığında onu kaldırın:</span><span class="sxs-lookup"><span data-stu-id="fd831-220">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="fd831-221">Kapsayıcı Ayrıca parametreleri .NET Core uygulamasının yürütülmesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="fd831-221">The container also passes parameters into the execution of the .NET Core app.</span></span> <span data-ttu-id="fd831-222">.NET Core uygulamasının 3 ' te yalnızca 3 geçişine kadar saymasını bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="fd831-222">To instruct the .NET Core app to count only to 3 pass in 3.</span></span>

```console
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

<span data-ttu-id="fd831-223">İle `docker run -it` , <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, bu da kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="fd831-223">With `docker run -it`, the <kbd>Ctrl+C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="fd831-224">`--rm`Parametre sağlandığı için, işlem durdurulduğunda kapsayıcı otomatik olarak silinir.</span><span class="sxs-lookup"><span data-stu-id="fd831-224">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="fd831-225">Mevcut olmadığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="fd831-225">Verify that it doesn't exist:</span></span>

```console
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="fd831-226">GIRIŞ noktasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="fd831-226">Change the ENTRYPOINT</span></span>

<span data-ttu-id="fd831-227">`docker run`Komut ayrıca `ENTRYPOINT` *dockerfile* ' dan komutu değiştirmenize ve yalnızca bu kapsayıcı için, başka bir şey çalıştırmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="fd831-227">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="fd831-228">Örneğin, veya çalıştırmak için aşağıdaki komutu kullanın `bash` `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="fd831-228">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="fd831-229">Komutu gereken şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="fd831-229">Edit the command as necessary.</span></span>

#### <a name="windows"></a>[<span data-ttu-id="fd831-230">Windows</span><span class="sxs-lookup"><span data-stu-id="fd831-230">Windows</span></span>](#tab/windows)

<span data-ttu-id="fd831-231">Bu örnekte, `ENTRYPOINT` olarak değiştirilir `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="fd831-231">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="fd831-232">İşlemi sonlandırmak ve kapsayıcıyı durdurmak için <kbd>CTRL + C</kbd> tuşlarına basıldığında.</span><span class="sxs-lookup"><span data-stu-id="fd831-232"><kbd>Ctrl+C</kbd> is pressed to end the process and stop the container.</span></span>

```console
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[<span data-ttu-id="fd831-233">Linux</span><span class="sxs-lookup"><span data-stu-id="fd831-233">Linux</span></span>](#tab/linux)

<span data-ttu-id="fd831-234">Bu örnekte, `ENTRYPOINT` olarak değiştirilir `bash` .</span><span class="sxs-lookup"><span data-stu-id="fd831-234">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="fd831-235">`exit`Komut, işlemi sonlandıran ve kapsayıcıyı durduran çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="fd831-235">The `exit` command is run which ends the process and stop the container.</span></span>

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a><span data-ttu-id="fd831-236">Gerekli komutlar</span><span class="sxs-lookup"><span data-stu-id="fd831-236">Essential commands</span></span>

<span data-ttu-id="fd831-237">Docker kapsayıcıları ve görüntüleri oluşturan, yöneten ve bunlarla etkileşim kuran birçok farklı komuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fd831-237">Docker has many different commands that create, manage, and interact with containers and images.</span></span> <span data-ttu-id="fd831-238">Bu Docker komutları, Kapsayıcılarınızı yönetmek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="fd831-238">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="fd831-239">docker build</span><span class="sxs-lookup"><span data-stu-id="fd831-239">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="fd831-240">Docker çalıştırma</span><span class="sxs-lookup"><span data-stu-id="fd831-240">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="fd831-241">docker ps</span><span class="sxs-lookup"><span data-stu-id="fd831-241">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="fd831-242">Docker durdur</span><span class="sxs-lookup"><span data-stu-id="fd831-242">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="fd831-243">Docker RM</span><span class="sxs-lookup"><span data-stu-id="fd831-243">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="fd831-244">Docker rmi</span><span class="sxs-lookup"><span data-stu-id="fd831-244">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="fd831-245">Docker görüntüsü</span><span class="sxs-lookup"><span data-stu-id="fd831-245">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="fd831-246">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="fd831-246">Clean up resources</span></span>

<span data-ttu-id="fd831-247">Bu öğreticide kapsayıcılar ve görüntüler oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="fd831-247">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="fd831-248">İsterseniz, bu kaynakları silin.</span><span class="sxs-lookup"><span data-stu-id="fd831-248">If you want, delete these resources.</span></span> <span data-ttu-id="fd831-249">İçin aşağıdaki komutları kullanın</span><span class="sxs-lookup"><span data-stu-id="fd831-249">Use the following commands to</span></span>

01. <span data-ttu-id="fd831-250">Tüm kapsayıcıları Listele</span><span class="sxs-lookup"><span data-stu-id="fd831-250">List all containers</span></span>

    ```console
    docker ps -a
    ```

02. <span data-ttu-id="fd831-251">Adına göre çalışan kapsayıcıları durdurun.</span><span class="sxs-lookup"><span data-stu-id="fd831-251">Stop containers that are running by their name.</span></span>

    ```console
    docker stop counter-image
    ```

03. <span data-ttu-id="fd831-252">Kapsayıcıyı silme</span><span class="sxs-lookup"><span data-stu-id="fd831-252">Delete the container</span></span>

    ```console
    docker rm counter-image
    ```

<span data-ttu-id="fd831-253">Sonra, makinenizde artık istemediğiniz görüntüleri silin.</span><span class="sxs-lookup"><span data-stu-id="fd831-253">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="fd831-254">*Dockerfile* dosyanız tarafından oluşturulan görüntüyü silin ve ardından *dockerfile* ' ın dayandığı .NET Core görüntüsünü silin.</span><span class="sxs-lookup"><span data-stu-id="fd831-254">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="fd831-255">**Görüntü kimliğini** veya **Depo: etiketli dize etiketini** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd831-255">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="fd831-256">`docker images`Yüklenen görüntülerin listesini görmek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fd831-256">Use the `docker images` command to see a list of images installed.</span></span>

> [!TIP]
> <span data-ttu-id="fd831-257">Görüntü dosyaları büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd831-257">Image files can be large.</span></span> <span data-ttu-id="fd831-258">Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="fd831-258">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="fd831-259">Bu çalışma zamanına göre diğer görüntüleri oluşturmayı planlıyorsanız, genellikle temel görüntüleri çalışma zamanı yüklü olarak tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd831-259">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fd831-260">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="fd831-260">Next steps</span></span>

- [<span data-ttu-id="fd831-261">ASP.NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="fd831-261">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="fd831-262">ASP.NET Core mikro hizmet öğreticisini deneyin.</span><span class="sxs-lookup"><span data-stu-id="fd831-262">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="fd831-263">Kapsayıcıları destekleyen Azure hizmetlerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="fd831-263">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="fd831-264">Dockerfile komutları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="fd831-264">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="fd831-265">Visual Studio için kapsayıcı araçlarını keşfet</span><span class="sxs-lookup"><span data-stu-id="fd831-265">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)

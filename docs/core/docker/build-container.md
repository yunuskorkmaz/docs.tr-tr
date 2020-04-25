---
title: Docker öğreticisi ile uygulama Kapsayıcılı hale getirme
description: Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edineceksiniz.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 03c0d8824eefd5956b43bc0b812abb0d5b7688ed
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140826"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="2bd0e-103">Öğretici: bir .NET Core uygulamasını Kapsayıize edin</span><span class="sxs-lookup"><span data-stu-id="2bd0e-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="2bd0e-104">Bu öğretici, .NET Core uygulamanızı içeren bir Docker görüntüsü oluşturmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="2bd0e-105">Görüntü, yerel geliştirme ortamınız, özel bulut veya genel bulutunuz için kapsayıcılar oluşturmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="2bd0e-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="2bd0e-107">Basit bir .NET Core uygulaması oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="2bd0e-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="2bd0e-108">.NET Core için Dockerfile oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="2bd0e-109">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-109">Build a Docker image</span></span>
> - <span data-ttu-id="2bd0e-110">Docker kapsayıcısı oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-110">Create and run a Docker container</span></span>

<span data-ttu-id="2bd0e-111">Docker kapsayıcısının bir .NET Core uygulaması için görevleri oluşturup dağıtduklarını anlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="2bd0e-112">*Docker platformu* , uygulamaları *Docker görüntüleri*olarak hızlı bir şekilde oluşturmak ve paketlemek için *Docker altyapısını* kullanır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="2bd0e-113">Bu görüntüler, katmanlı bir kapsayıcıda dağıtılacak ve çalıştırılacak *Dockerfile* biçiminde yazılır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!WARNING]
> <span data-ttu-id="2bd0e-114">**Bu öğretici ASP.NET Core uygulamalar için değildir.**</span><span class="sxs-lookup"><span data-stu-id="2bd0e-114">**This tutorial isn't for ASP.NET Core apps.**</span></span> <span data-ttu-id="2bd0e-115">ASP.NET Core kullanıyorsanız, [bir ASP.NET Core uygulama](/aspnet/core/host-and-deploy/docker/building-net-docker-images) öğreticisini nasıl kapsayıtabilecek öğrenin makalesini okuyun.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-115">If you're using ASP.NET Core, read the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2bd0e-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="2bd0e-116">Prerequisites</span></span>

<span data-ttu-id="2bd0e-117">Aşağıdaki önkoşulları yükler:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-117">Install the following prerequisites:</span></span>

- <span data-ttu-id="2bd0e-118">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="2bd0e-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="2bd0e-119">.NET Core yüklüyse, kullanmakta olduğunuz SDK 'yı öğrenmek `dotnet --info` için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-119">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="2bd0e-120">Docker Community sürümü</span><span class="sxs-lookup"><span data-stu-id="2bd0e-120">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="2bd0e-121">*Dockerfile* ve .NET Core örnek uygulaması için geçici çalışma klasörü.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-121">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="2bd0e-122">Bu öğreticide, *Docker-Working* adı çalışma klasörü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-122">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="2bd0e-123">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-123">Create .NET Core app</span></span>

<span data-ttu-id="2bd0e-124">Docker kapsayıcısının çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-124">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="2bd0e-125">Terminalinizi açın, henüz yapmadıysanız bir çalışma klasörü oluşturun ve bunu girin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-125">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="2bd0e-126">Çalışma klasöründe, *uygulama*adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-126">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="2bd0e-127">Klasör ağaclarınız şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-127">Your folder tree will look like the following:</span></span>

```
docker-working
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.dgspec.json
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="2bd0e-128">Komut `dotnet new` , *uygulama* adlı yeni bir klasör oluşturur ve bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-128">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="2bd0e-129">*Uygulama* klasörünü girip komutunu `dotnet run`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-129">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="2bd0e-130">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-130">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="2bd0e-131">Varsayılan şablon, terminale yazdıran ve ardından çıkış yapan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-131">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="2bd0e-132">Bu öğretici için süresiz olarak döngü yapan bir uygulama kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-132">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="2bd0e-133">*Program.cs* dosyasını bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-133">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="2bd0e-134">Şu anda şu kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-134">It should currently look like the following code:</span></span>

```csharp
using System;

namespace myapp
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

<span data-ttu-id="2bd0e-135">Dosyayı her saniye sayı sayan aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-135">Replace the file with the following code that counts numbers every second:</span></span>

```csharp
using System;

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="2bd0e-136">Dosyayı kaydedin ve ile `dotnet run`programı test edin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-136">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="2bd0e-137">Bu uygulamanın süresiz olarak çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-137">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="2bd0e-138">Durdurmak için <kbd>CTRL</kbd>+<kbd>C</kbd> Cancel komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-138">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="2bd0e-139">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-139">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="2bd0e-140">Uygulama için komut satırına bir sayı geçirirseniz, bu miktarı yalnızca bu miktara göre sayılır ve ardından çıkış olur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-140">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="2bd0e-141">Beş olarak saymak `dotnet run -- 5` için deneyin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-141">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="2bd0e-142">Sonrasında `--` herhangi bir parametre `dotnet run` komutuna geçirilmez ve bunun yerine uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-142">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="2bd0e-143">.NET Core uygulaması Yayımla</span><span class="sxs-lookup"><span data-stu-id="2bd0e-143">Publish .NET Core app</span></span>

<span data-ttu-id="2bd0e-144">.NET Core uygulamanızı Docker görüntüsüne eklemeden önce yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-144">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="2bd0e-145">Kapsayıcının, başlatıldığında uygulamanın yayımlanmış sürümünü çalıştırmasını sağlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-145">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="2bd0e-146">Çalışma klasöründen, örnek kaynak kodu ile *uygulama* klasörünü girin ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-146">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="2bd0e-147">Bu komut, uygulamanızı *Yayımla* klasörüne derler.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-147">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="2bd0e-148">Çalışma klasöründeki *Yayımla* klasörünün yolu`.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="2bd0e-148">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="2bd0e-149">*App* klasöründen, *MyApp. dll* dosyasının oluşturulduğunu doğrulamak için Yayımla klasörünün bir dizin listesini alın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-149">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span>

```console
> dir bin\Release\netcoreapp3.1\publish

    Directory:  C:\docker-working\app\bin\Release\netcoreapp3.1\publish

01/09/2020  11:41 AM    <DIR>          .
01/09/2020  11:41 AM    <DIR>          ..
01/09/2020  11:41 AM               407 myapp.deps.json
01/09/2020  12:15 PM             4,608 myapp.dll
01/09/2020  12:15 PM           169,984 myapp.exe
01/09/2020  12:15 PM               736 myapp.pdb
01/09/2020  11:41 AM               154 myapp.runtimeconfig.json
```

<span data-ttu-id="2bd0e-150">Linux veya macOS kullanıyorsanız, bir dizin listesi almak için `ls` komutunu kullanın ve *MyApp. dll* dosyasının oluşturulduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-150">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="2bd0e-151">Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-151">Create the Dockerfile</span></span>

<span data-ttu-id="2bd0e-152">*Dockerfile* dosyası `docker build` komut tarafından bir kapsayıcı görüntüsü oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-152">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="2bd0e-153">Bu dosya, uzantısı olmayan *Dockerfile* adlı bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-153">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="2bd0e-154">Terminalinizde, başlangıçta oluşturduğunuz çalışma klasörüne bir dizin geri gidin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-154">In your terminal, navigate back one directory to the working folder you created at the start.</span></span> <span data-ttu-id="2bd0e-155">Çalışma klasörünüzde *Dockerfile* adlı bir dosya oluşturun ve dosyayı bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-155">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="2bd0e-156">Kapsayıcılı olduğunuz uygulamanın türüne bağlı olarak, ASP.NET Core çalışma zamanını veya .NET Core çalışma zamanını seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-156">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="2bd0e-157">Şüpheli olduğunda, .NET Core çalışma zamanını içeren ASP.NET Core çalışma zamanını seçin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-157">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="2bd0e-158">Bu öğretici ASP.NET Core çalışma zamanı görüntüsünü kullanır, ancak önceki bölümlerde oluşturulan uygulama bir .NET Core uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-158">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="2bd0e-159">ASP.NET Core çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="2bd0e-159">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="2bd0e-160">.NET Core çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="2bd0e-160">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="2bd0e-161">Komut `FROM` , Docker 'a belirtilen depodan etiketlenen **3,1** görüntüsünü çekmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-161">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="2bd0e-162">SDK 'nizin hedeflediği çalışma zamanıyla eşleşen çalışma zamanı sürümünü çekdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-162">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="2bd0e-163">Örneğin, önceki bölümde oluşturulan uygulama .NET Core 3,1 SDK 'sını ve *Dockerfile* içinde başvurulan temel görüntüyü **3,1**ile etiketledi.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-163">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="2bd0e-164">*Dockerfile* dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="2bd0e-165">Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="2bd0e-166">Daha derin düzey dosya ve klasörlerin bazıları, makalede yer kazanmak için kesildi:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp3.1
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.exe
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="2bd0e-167">Terminalinizden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="2bd0e-168">Docker, *Dockerfile*dosyasındaki her satırı işleyecek.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="2bd0e-169">`.` Komutunda Docker 'ın bir *dockerfile dosyasını*bulmak için geçerli klasörü kullanmasını `docker build` söyler.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="2bd0e-170">Bu komut, görüntüyü oluşturur ve bu görüntüyü işaret eden **MyImage** adlı bir yerel depo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="2bd0e-171">Bu komut tamamlandıktan sonra, yüklenen `docker images` görüntülerin listesini görmek için komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              54240314fe71        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 54240314fe71        4 weeks ago         346MB
```

<span data-ttu-id="2bd0e-172">İki görüntünün aynı **görüntü kimliği** değerini paylaştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="2bd0e-173">*Dockerfile* 'daki tek komut yeni görüntünün varolan bir görüntüye dayandırdığı için, her iki görüntü arasında değer aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="2bd0e-174">*Dockerfile dosyasına*iki komut ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="2bd0e-175">Her komut, **MyImage** Repository girişinin işaret ettiği görüntüyü temsil eden son komutla yeni bir görüntü katmanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-175">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

WORKDIR /app

ENTRYPOINT ["dotnet", "myapp.dll"]
```

<span data-ttu-id="2bd0e-176">Komut `COPY` , Docker 'a bilgisayarınızdaki belirtilen klasörü kapsayıcıda bir klasöre kopyalamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="2bd0e-177">Bu örnekte, *Publish* klasörü kapsayıcıda *uygulama* adlı bir klasöre kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-177">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="2bd0e-178">`WORKDIR` Komut, kapsayıcının içindeki **geçerli dizini** *uygulama*olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-178">The `WORKDIR` command changes the **current directory** inside of the container to *app*.</span></span>

<span data-ttu-id="2bd0e-179">Sonraki komut `ENTRYPOINT`, Docker öğesine kapsayıcıyı yürütülebilir olarak çalışacak şekilde yapılandırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-179">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="2bd0e-180">Kapsayıcı başladığında, `ENTRYPOINT` komutu çalışır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-180">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="2bd0e-181">Bu komut sona erdiğinde kapsayıcı otomatik olarak durur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-181">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="2bd0e-182">Terminalinizden komutunu çalıştırın `docker build -t myimage -f Dockerfile .` ve komut tamamlandığında komutunu çalıştırın `docker images`.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-182">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.121MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 54240314fe71
Step 2/4 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 1e05ea8b3ef5
Step 3/4 : WORKDIR /app
 ---> Running in 8c8f710e6292
Removing intermediate container 8c8f710e6292
 ---> 31575599f7dc
Step 4/4 : ENTRYPOINT ["dotnet", "myapp.dll"]
 ---> Running in 93851322fb76
Removing intermediate container 93851322fb76
 ---> e496e8b22d02
Successfully built e496e8b22d02
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              e496e8b22d02        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 54240314fe71        4 weeks ago         346MB
```

<span data-ttu-id="2bd0e-183">*Dockerfile* 'daki her komut bir katman oluşturdu ve BIR **görüntü kimliği**oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-183">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="2bd0e-184">Son **görüntü kimliği** (sizinki farklı olacak) **ddcc6646461b** ve bir sonraki adımda bu görüntüye göre bir kapsayıcı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-184">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="2bd0e-185">Bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-185">Create a container</span></span>

<span data-ttu-id="2bd0e-186">Artık uygulamanızı içeren bir görüntünüz olduğuna göre, bir kapsayıcı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-186">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="2bd0e-187">Bir kapsayıcıyı iki şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-187">You can create a container in two ways.</span></span> <span data-ttu-id="2bd0e-188">İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-188">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
9222af24353f42bab6c13e01a0a64ef2c915cad27bdc46ffa32380581de11e91
```

<span data-ttu-id="2bd0e-189">Yukarıdaki `docker create` komut, **MyImage** görüntüsünü temel alan bir kapsayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-189">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="2bd0e-190">Bu komutun çıktısı, oluşturulan kapsayıcının **KAPSAYıCı kimliğini** (sizinki farklı olacak) gösterir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-190">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="2bd0e-191">*Tüm* kapsayıcıların listesini görmek için `docker ps -a` komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-191">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS        PORTS   NAMES
9222af24353f        myimage             "dotnet myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="2bd0e-192">Kapsayıcıyı yönetme</span><span class="sxs-lookup"><span data-stu-id="2bd0e-192">Manage the container</span></span>

<span data-ttu-id="2bd0e-193">Her kapsayıcıya, bu kapsayıcı örneğine başvurmak için kullanabileceğiniz bir rastgele ad atanır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-193">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="2bd0e-194">Örneğin, otomatik olarak oluşturulan kapsayıcı **gallant_lehmann** adı (sizinki farklı olacaktır) seçti ve bu ad kapsayıcıyı başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-194">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="2bd0e-195">`docker create --name` Parametresini kullanarak otomatik adı belirli bir ile geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-195">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="2bd0e-196">Aşağıdaki örnek, kapsayıcıyı başlatmak `docker start` için komutunu kullanır ve sonra yalnızca çalıştıran kapsayıcıları göstermek için `docker ps` komutunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-196">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS         PORTS   NAMES
9222af24353f        myimage             "dotnet myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="2bd0e-197">Benzer şekilde, `docker stop` komut kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-197">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="2bd0e-198">Aşağıdaki örnek, kapsayıcıyı durdurmak `docker stop` için komutunu kullanır ve ardından hiçbir kapsayıcının çalışmadığını göstermek için `docker ps` komutunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-198">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="2bd0e-199">Bir kapsayıcıya bağlanma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-199">Connect to a container</span></span>

<span data-ttu-id="2bd0e-200">Bir kapsayıcı çalışmaya başladıktan sonra çıktıyı görmek için bu sunucuya bağlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-200">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="2bd0e-201">`docker start` Ve `docker attach` komutlarını kullanarak kapsayıcıyı başlatın ve çıkış akışına göz atın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-201">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="2bd0e-202">Bu örnekte, <kbd>CTRL + C</kbd> tuş vuruşu, çalışan kapsayıcıyı ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-202">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="2bd0e-203">Bu tuş vuruşu, kapsayıcıyı durduran kapsayıcıyı gerçekten sonlandırarak işlemden çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-203">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="2bd0e-204">`--sig-proxy=false` Parametresi, <kbd>CTRL + C</kbd> 'nin kapsayıcıdaki işlemi durdurmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-204">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="2bd0e-205">Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saymakta olduğunu doğrulamak için yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-205">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker attach --sig-proxy=false gallant_lehmann
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false gallant_lehmann
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="2bd0e-206">Kapsayıcı silme</span><span class="sxs-lookup"><span data-stu-id="2bd0e-206">Delete a container</span></span>

<span data-ttu-id="2bd0e-207">Bu makalenin amaçları doğrultusunda, kapsayıcıların hiçbir şey yapmadan asılı istememeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-207">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="2bd0e-208">Daha önce oluşturduğunuz kapsayıcıyı silin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-208">Delete the container you previously created.</span></span> <span data-ttu-id="2bd0e-209">Kapsayıcı çalışıyorsa durdurun.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-209">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="2bd0e-210">Aşağıdaki örnekte tüm kapsayıcılar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-210">The following example lists all containers.</span></span> <span data-ttu-id="2bd0e-211">Ardından, kapsayıcıyı silmek `docker rm` için komutunu kullanır ve ardından çalışan kapsayıcılar için ikinci bir kez kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-211">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS     PORTS   NAMES
9222af24353f        myimage             "dotnet myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="2bd0e-212">Tek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-212">Single run</span></span>

<span data-ttu-id="2bd0e-213">Docker, kapsayıcıyı `docker run` tek bir komut olarak oluşturup çalıştırmak için komutunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-213">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="2bd0e-214">Bu komut, ve daha sonra `docker create` `docker start`çalıştırma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-214">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="2bd0e-215">Kapsayıcı durdurulduğunda kapsayıcıyı otomatik olarak silmek için de bu komutu ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-215">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="2bd0e-216">Örneğin, ilk olarak `docker run -it --rm` iki şey yapmak için kullanın, kapsayıcıya bağlanmak için otomatik olarak geçerli terminali kullanın ve ardından kapsayıcı tamamlandığında onu kaldırın:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-216">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="2bd0e-217">İle `docker run -it`, <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, bu da kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-217">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="2bd0e-218">`--rm` Parametre sağlandığı için, işlem durdurulduğunda kapsayıcı otomatik olarak silinir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-218">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="2bd0e-219">Mevcut olmadığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-219">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="2bd0e-220">GIRIŞ noktasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="2bd0e-220">Change the ENTRYPOINT</span></span>

<span data-ttu-id="2bd0e-221">`docker run` Komut ayrıca *dockerfile* ' dan `ENTRYPOINT` komutu değiştirmenize ve yalnızca bu kapsayıcı için, başka bir şey çalıştırmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-221">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="2bd0e-222">Örneğin, veya `bash` `cmd.exe`çalıştırmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-222">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="2bd0e-223">Komutu gereken şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-223">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="2bd0e-224">Windows</span><span class="sxs-lookup"><span data-stu-id="2bd0e-224">Windows</span></span>

<span data-ttu-id="2bd0e-225">Bu örnekte, `ENTRYPOINT` olarak `cmd.exe`değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-225">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="2bd0e-226"><kbd>CTRL</kbd>+İşlemi sonlandırmak ve kapsayıcıyı durdurmak için CTRL<kbd>C</kbd> 'ye basıldı.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-226"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

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

#### <a name="linux"></a><span data-ttu-id="2bd0e-227">Linux</span><span class="sxs-lookup"><span data-stu-id="2bd0e-227">Linux</span></span>

<span data-ttu-id="2bd0e-228">Bu örnekte, `ENTRYPOINT` olarak `bash`değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-228">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="2bd0e-229">`quit` Komut, işlemi sonlandıran ve kapsayıcıyı durduran çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-229">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="2bd0e-230">Gerekli komutlar</span><span class="sxs-lookup"><span data-stu-id="2bd0e-230">Essential commands</span></span>

<span data-ttu-id="2bd0e-231">Docker, kapsayıcınıza ve görüntülerinize ne yapmak istediğinizi kapsayan birçok farklı komuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-231">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="2bd0e-232">Bu Docker komutları, Kapsayıcılarınızı yönetmek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="2bd0e-232">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="2bd0e-233">docker build</span><span class="sxs-lookup"><span data-stu-id="2bd0e-233">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="2bd0e-234">Docker çalıştırma</span><span class="sxs-lookup"><span data-stu-id="2bd0e-234">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="2bd0e-235">docker ps</span><span class="sxs-lookup"><span data-stu-id="2bd0e-235">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="2bd0e-236">Docker durdur</span><span class="sxs-lookup"><span data-stu-id="2bd0e-236">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="2bd0e-237">Docker RM</span><span class="sxs-lookup"><span data-stu-id="2bd0e-237">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="2bd0e-238">Docker rmi</span><span class="sxs-lookup"><span data-stu-id="2bd0e-238">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="2bd0e-239">Docker görüntüsü</span><span class="sxs-lookup"><span data-stu-id="2bd0e-239">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="2bd0e-240">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="2bd0e-240">Clean up resources</span></span>

<span data-ttu-id="2bd0e-241">Bu öğreticide kapsayıcılar ve görüntüler oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-241">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="2bd0e-242">İsterseniz, bu kaynakları silin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-242">If you want, delete these resources.</span></span> <span data-ttu-id="2bd0e-243">İçin aşağıdaki komutları kullanın</span><span class="sxs-lookup"><span data-stu-id="2bd0e-243">Use the following commands to</span></span>

01. <span data-ttu-id="2bd0e-244">Tüm kapsayıcıları Listele</span><span class="sxs-lookup"><span data-stu-id="2bd0e-244">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="2bd0e-245">Çalıştıran kapsayıcıları durdurun.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-245">Stop containers that are running.</span></span> <span data-ttu-id="2bd0e-246">, `CONTAINER_NAME` Kapsayıcıya otomatik olarak atanan adı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-246">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="2bd0e-247">Kapsayıcıyı silme</span><span class="sxs-lookup"><span data-stu-id="2bd0e-247">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="2bd0e-248">Sonra, makinenizde artık istemediğiniz görüntüleri silin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-248">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="2bd0e-249">*Dockerfile* dosyanız tarafından oluşturulan görüntüyü silin ve ardından *dockerfile* ' ın dayandığı .NET Core görüntüsünü silin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-249">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="2bd0e-250">**Görüntü kimliğini** veya **Depo: etiketli dize etiketini** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-250">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="2bd0e-251">Yüklenen görüntülerin `docker images` listesini görmek için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-251">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="2bd0e-252">Görüntü dosyaları büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-252">Image files can be large.</span></span> <span data-ttu-id="2bd0e-253">Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-253">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="2bd0e-254">Bu çalışma zamanına göre diğer görüntüleri oluşturmayı planlıyorsanız, genellikle temel görüntüleri çalışma zamanı yüklü olarak tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-254">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2bd0e-255">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="2bd0e-255">Next steps</span></span>

- [<span data-ttu-id="2bd0e-256">ASP.NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-256">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="2bd0e-257">ASP.NET Core mikro hizmet öğreticisini deneyin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-257">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="2bd0e-258">Kapsayıcıları destekleyen Azure hizmetlerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-258">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="2bd0e-259">Dockerfile komutları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="2bd0e-259">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="2bd0e-260">Visual Studio için kapsayıcı araçlarını keşfet</span><span class="sxs-lookup"><span data-stu-id="2bd0e-260">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)

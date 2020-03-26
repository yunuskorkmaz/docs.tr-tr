---
title: Docker öğreticisiyle bir uygulamayı konteynerleştirin
description: Bu eğitimde, Docker ile bir .NET Core uygulamasını nasıl kaplaştırabileceğinizi öğreneceksiniz.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 8be12792e4a9e8511dba87e657f700cc4ec97a16
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546581"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="1beb2-103">Öğretici: Containerize bir .NET Core uygulaması</span><span class="sxs-lookup"><span data-stu-id="1beb2-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="1beb2-104">Bu öğretici, .NET Core uygulamanızı içeren bir Docker görüntüsünü nasıl oluşturabileceğinizi öğretir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="1beb2-105">Görüntü, yerel geliştirme ortamınız, özel bulutunuz veya genel bulutunuz için kapsayıcılar oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="1beb2-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="1beb2-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="1beb2-107">Basit bir .NET Core uygulaması oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="1beb2-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="1beb2-108">.NET Core için Dockerfile oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1beb2-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="1beb2-109">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="1beb2-109">Build a Docker image</span></span>
> - <span data-ttu-id="1beb2-110">Docker kapsayıcısı oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1beb2-110">Create and run a Docker container</span></span>

<span data-ttu-id="1beb2-111">Docker kapsayıcısını anlayacak ve .NET Core uygulaması için görevleri dağıtacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1beb2-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="1beb2-112">*Docker platformu,* *docker görüntüleri*olarak uygulamaları hızlı bir şekilde oluşturmak ve paketlemek için *Docker motorını* kullanır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="1beb2-113">Bu görüntüler, katmanlı bir kapsayıcıda dağıtılmak ve çalıştırılmak üzere *Dockerfile* biçiminde yazılır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!WARNING]
> <span data-ttu-id="1beb2-114">**Bu öğretici ASP.NET Core uygulamaları için değildir.**</span><span class="sxs-lookup"><span data-stu-id="1beb2-114">**This tutorial isn't for ASP.NET Core apps.**</span></span> <span data-ttu-id="1beb2-115">ASP.NET Core kullanıyorsanız, ASP.NET Core uygulama öğreticisini [nasıl kaplaştırabileceğinizi öğrenin'i](/aspnet/core/host-and-deploy/docker/building-net-docker-images) okuyun.</span><span class="sxs-lookup"><span data-stu-id="1beb2-115">If you're using ASP.NET Core, read the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1beb2-116">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="1beb2-116">Prerequisites</span></span>

<span data-ttu-id="1beb2-117">Aşağıdaki ön koşulları yükleyin:</span><span class="sxs-lookup"><span data-stu-id="1beb2-117">Install the following prerequisites:</span></span>

- <span data-ttu-id="1beb2-118">[.NET Çekirdek 3.1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="1beb2-118">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="1beb2-119">.NET Core yüklüyseniz, hangi `dotnet --info` SDK'yı kullandığınızı belirlemek için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-119">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="1beb2-120">Docker Topluluk Sürümü</span><span class="sxs-lookup"><span data-stu-id="1beb2-120">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="1beb2-121">*Dockerfile* ve .NET Core örnek uygulaması için geçici bir çalışma klasörü.</span><span class="sxs-lookup"><span data-stu-id="1beb2-121">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="1beb2-122">Bu öğreticide, *docker-working* adı çalışma klasörü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-122">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="1beb2-123">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="1beb2-123">Create .NET Core app</span></span>

<span data-ttu-id="1beb2-124">Docker konteynerinin çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-124">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="1beb2-125">Terminalinizi açın, çalışma klasörü oluşturun, henüz yapmadıysanız ve girin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-125">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="1beb2-126">Çalışma klasöründe, *uygulama*adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1beb2-126">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="1beb2-127">Klasör ağacınız aşağıdaki gibi görünecektir:</span><span class="sxs-lookup"><span data-stu-id="1beb2-127">Your folder tree will look like the following:</span></span>

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

<span data-ttu-id="1beb2-128">`dotnet new` Komut, *uygulama* adında yeni bir klasör oluşturur ve bir "Hello World" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-128">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="1beb2-129">*Uygulama* klasörünü girin ve `dotnet run`komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-129">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="1beb2-130">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="1beb2-130">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="1beb2-131">Varsayılan şablon, terminale yazdırılan ve sonra çıkan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-131">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="1beb2-132">Bu öğretici için, süresiz döngüler bir uygulama kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1beb2-132">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="1beb2-133">*Program.cs* dosyasını metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-133">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="1beb2-134">Şu anda aşağıdaki kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="1beb2-134">It should currently look like the following code:</span></span>

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

<span data-ttu-id="1beb2-135">Dosyayı, her saniye sayıları sayan aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="1beb2-135">Replace the file with the following code that counts numbers every second:</span></span>

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

<span data-ttu-id="1beb2-136">Dosyayı kaydedin ve `dotnet run`programı tekrar .</span><span class="sxs-lookup"><span data-stu-id="1beb2-136">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="1beb2-137">Bu uygulamanın süresiz olarak çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-137">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="1beb2-138">Durdurmak için <kbd>CTRL</kbd>+<kbd>C'yi</kbd> iptal et komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-138">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="1beb2-139">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="1beb2-139">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="1beb2-140">Komut satırındaki bir numarayı uygulamaya geçirirseniz, yalnızca bu tutara kadar sayılır ve sonra çıkar.</span><span class="sxs-lookup"><span data-stu-id="1beb2-140">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="1beb2-141">`dotnet run -- 5` Beşe kadar saymayı dene.</span><span class="sxs-lookup"><span data-stu-id="1beb2-141">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="1beb2-142">Sonra `--` gelen parametreler komuta `dotnet run` geçirilmeyecek ve bunun yerine uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-142">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="1beb2-143">.NET Core uygulamasını yayınla</span><span class="sxs-lookup"><span data-stu-id="1beb2-143">Publish .NET Core app</span></span>

<span data-ttu-id="1beb2-144">.NET Core uygulamanızı Docker resmine eklemeden önce yayınlayın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-144">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="1beb2-145">Kapsayıcının başlatıldığında uygulamanın yayımlanmış sürümünü çalıştırdığından emin olmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="1beb2-145">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="1beb2-146">Çalışma klasöründen, örnek kaynak koduyla *uygulama* klasörüne girin ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1beb2-146">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="1beb2-147">Bu komut, uygulamanızı *yayımlama* klasörüne derler.</span><span class="sxs-lookup"><span data-stu-id="1beb2-147">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="1beb2-148">Çalışma klasöründen *yayımlama* klasörüne giden yol,`.\app\bin\Release\netcoreapp3.1\publish\`</span><span class="sxs-lookup"><span data-stu-id="1beb2-148">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="1beb2-149">*Uygulama* klasöründen, *myapp.dll* dosyasının oluşturulduğunu doğrulamak için yayımlama klasörünün dizin listesini alın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-149">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span>

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

<span data-ttu-id="1beb2-150">Linux veya macOS kullanıyorsanız, bir `ls` dizin listesi almak ve *myapp.dll* dosyasının oluşturulduğunu doğrulamak için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-150">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="1beb2-151">Dockerfile'ı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1beb2-151">Create the Dockerfile</span></span>

<span data-ttu-id="1beb2-152">*Dockerfile* dosyası `docker build` bir kapsayıcı görüntüsü oluşturmak için komut tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-152">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="1beb2-153">Bu dosya, uzantısı olmayan *Dockerfile* adlı bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-153">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="1beb2-154">Terminalinizde, başlangıçta oluşturduğunuz çalışma klasörüne bir dizin gidin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-154">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="1beb2-155">Çalışma klasörünüzde *Dockerfile* adında bir dosya oluşturun ve bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-155">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="1beb2-156">Kapsayıcıhale edeceğiniz uygulamanın türüne bağlı olarak, ASP.NET Çekirdek çalışma zamanını veya .NET Core çalışma zamanını seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="1beb2-156">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="1beb2-157">Şüpheye düştüğünüzde, .NET Core çalışma süresini içeren ASP.NET Core çalışma saatini seçin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-157">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="1beb2-158">Bu öğretici, ASP.NET Core çalışma zamanı görüntüsünü kullanır, ancak önceki bölümlerde oluşturulan uygulama bir .NET Core uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-158">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="1beb2-159">ASP.NET Core çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="1beb2-159">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="1beb2-160">.NET Çekirdek çalışma süresi</span><span class="sxs-lookup"><span data-stu-id="1beb2-160">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="1beb2-161">Komut, Docker'a `FROM` belirtilen depodan **3.1** etiketli görüntüyü aşağı çekmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="1beb2-161">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="1beb2-162">SDK'nız tarafından hedeflenen çalışma zamanı sürümüyle eşleşen çalışma zamanı sürümünü çektiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="1beb2-162">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="1beb2-163">Örneğin, önceki bölümde oluşturulan uygulama .NET Core 3.1 SDK kullanılır ve *Dockerfile'da* atıfta bulunulan temel resim **3.1**ile etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-163">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="1beb2-164">*Dockerfile* dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="1beb2-165">Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="1beb2-166">Makalede yer kazanmak için daha derin düzeydosya ve klasörlerden bazıları kesildi:</span><span class="sxs-lookup"><span data-stu-id="1beb2-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

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

<span data-ttu-id="1beb2-167">Terminalinizden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1beb2-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="1beb2-168">Docker, *Dockerdosyasındaki*her satırı işleyecek.</span><span class="sxs-lookup"><span data-stu-id="1beb2-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="1beb2-169">Komut, `.` `docker build` Docker'a geçerli klasörü kullanarak *Dockerfile'ı*bulmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="1beb2-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="1beb2-170">Bu komut görüntüyü oluşturur ve bu görüntüye işaret eden **myimage** adlı yerel bir depo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="1beb2-171">Bu komut bittikten `docker images` sonra, yüklü görüntülerin listesini görmek için çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="1beb2-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="1beb2-172">İki görüntünün aynı **GÖRÜNTÜ Kimliği** değerini paylaştığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="1beb2-173">*Dockerdosyasındaki* tek komut yeni görüntüyü varolan bir görüntüye dayandırmak olduğundan, değer her iki görüntü arasında da aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="1beb2-174">*Dockerfile'a*iki komut ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="1beb2-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="1beb2-175">Her komut, **myimage** depo giriş noktalarının görüntüye işaret ettiğini gösteren son komutla yeni bir görüntü katmanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-175">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="1beb2-176">Komut, Docker'a `COPY` bilgisayarınızda belirtilen klasörü kapsayıcıdaki bir klasöre kopyalamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="1beb2-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="1beb2-177">Bu örnekte, *yayımlama* klasörü kapsayıcıdaki *uygulama* adlı bir klasöre kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-177">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="1beb2-178">Bir sonraki `ENTRYPOINT`komut, Docker'a kapsayıcıyı çalıştırılabilir olarak çalışacak şekilde yapılandırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="1beb2-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="1beb2-179">Kapsayıcı `ENTRYPOINT` başladığında, komut çalışır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="1beb2-180">Bu komut sona erdiğinde, kapsayıcı otomatik olarak durur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="1beb2-181">Terminalinizden çalıştırın `docker build -t myimage -f Dockerfile .` ve komut bittiğinde `docker images`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  1.624MB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> 38db0eb8f648
Step 2/3 : COPY app/bin/Release/netcoreapp3.1/publish/ app/
 ---> 37873673e468
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in d8deb7b3aa9e
Removing intermediate container d8deb7b3aa9e
 ---> 0d602ca35c1d
Successfully built 0d602ca35c1d
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              0d602ca35c1d        4 seconds ago       346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="1beb2-182">*Dockerfile'daki* her komut bir katman oluşturdu ve bir **IMAGE ID**oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="1beb2-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="1beb2-183">Son **IMAGE ID** (sizinki farklı olacak) **ddcc6646461b** ve sonraki bu görüntüye dayalı bir kapsayıcı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="1beb2-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="1beb2-184">Bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="1beb2-184">Create a container</span></span>

<span data-ttu-id="1beb2-185">Artık uygulamanızı içeren bir resminiz olduğuna göre, bir kapsayıcı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1beb2-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="1beb2-186">Bir kapsayıcıyı iki şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1beb2-186">You can create a container in two ways.</span></span> <span data-ttu-id="1beb2-187">İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1beb2-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="1beb2-188">Yukarıdaki `docker create` **komut, myimage** görüntüsünü temel alan bir kapsayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="1beb2-189">Bu komutun çıktısı, oluşturulan **kapsayıcının KONTEYNER Kimliğini** (sizinki farklı olacaktır) gösterir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="1beb2-190">*Tüm* kapsayıcıların listesini görmek için `docker ps -a` aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1beb2-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="1beb2-191">Kapsayıcıyı yönetme</span><span class="sxs-lookup"><span data-stu-id="1beb2-191">Manage the container</span></span>

<span data-ttu-id="1beb2-192">Her kapsayıcıya, bu kapsayıcı örneğine başvurmak için kullanabileceğiniz rasgele bir ad atanır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="1beb2-193">Örneğin, otomatik olarak oluşturulan kapsayıcı **gallant_lehmann** (sizinki farklı olacak) adını seçer ve bu ad kapsayıcıyı başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-193">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="1beb2-194">`docker create --name` Parametreyi kullanarak otomatik adı belirli bir adla geçersiz kılarsınız.</span><span class="sxs-lookup"><span data-stu-id="1beb2-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="1beb2-195">Aşağıdaki örnek, `docker start` kapsayıcıyı başlatmak için komutu `docker ps` kullanır ve ardından yalnızca çalışan kapsayıcıları göstermek için komutu kullanır:</span><span class="sxs-lookup"><span data-stu-id="1beb2-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="1beb2-196">Benzer şekilde, `docker stop` komut kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="1beb2-197">Aşağıdaki örnek, `docker stop` kapsayıcıyı durdurmak için komutu `docker ps` kullanır ve sonra hiçbir kapsayıcının çalışmadığını göstermek için komutu kullanır:</span><span class="sxs-lookup"><span data-stu-id="1beb2-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="1beb2-198">Bir kapsayıcıya bağlanma</span><span class="sxs-lookup"><span data-stu-id="1beb2-198">Connect to a container</span></span>

<span data-ttu-id="1beb2-199">Bir kapsayıcı çalışmaya n ardından, çıktıyı görmek için ona bağlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1beb2-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="1beb2-200">Kapsayıcıyı `docker start` `docker attach` başlatmak ve çıkış akışına göz atmak için ve komutları kullanın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="1beb2-201">Bu örnekte, <kbd>CTRL + C</kbd> tuş vuruşu çalışan kapsayıcıdan ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-201">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="1beb2-202">Bu tuş vuruşu aslında kapsayıcıdaki işlemi sonlayabilir ve bu da kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-202">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="1beb2-203">`--sig-proxy=false` <kbd>Parametre, CTRL + C'nin</kbd> kapsayıcıdaki işlemi durdurmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1beb2-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="1beb2-204">Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saydığını doğrulamak için yeniden takın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

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

### <a name="delete-a-container"></a><span data-ttu-id="1beb2-205">Kapsayıcı silme</span><span class="sxs-lookup"><span data-stu-id="1beb2-205">Delete a container</span></span>

<span data-ttu-id="1beb2-206">Bu makalenin amaçları için sadece hiçbir şey yapmadan etrafında asılı konteyner istemiyorum.</span><span class="sxs-lookup"><span data-stu-id="1beb2-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="1beb2-207">Daha önce oluşturduğunuz kapsayıcıyı silin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-207">Delete the container you previously created.</span></span> <span data-ttu-id="1beb2-208">Kapsayıcı çalışıyorsa, durdurun.</span><span class="sxs-lookup"><span data-stu-id="1beb2-208">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="1beb2-209">Aşağıdaki örnekte tüm kapsayıcılar listelenebedilir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-209">The following example lists all containers.</span></span> <span data-ttu-id="1beb2-210">Daha sonra `docker rm` kapsayıcıyı silmek için komutu kullanır ve ardından çalışan kapsayıcılar için ikinci kez denetler.</span><span class="sxs-lookup"><span data-stu-id="1beb2-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="1beb2-211">Tek çalışma</span><span class="sxs-lookup"><span data-stu-id="1beb2-211">Single run</span></span>

<span data-ttu-id="1beb2-212">Docker, `docker run` kapsayıcıyı tek bir komut olarak oluşturma ve çalıştırma komutunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="1beb2-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="1beb2-213">Bu komut, çalıştırma `docker create` ve sonra `docker start`gereksinimi ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="1beb2-214">Kapsayıcı durduğunda kapsayıcıyı otomatik olarak silmek için bu komutu da ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1beb2-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="1beb2-215">Örneğin, iki `docker run -it --rm` şey yapmak için kullanın, ilk olarak, kapsayıcıya bağlanmak için geçerli terminali otomatik olarak kullanın ve sonra kapsayıcı bittiğinde, kaldırın:</span><span class="sxs-lookup"><span data-stu-id="1beb2-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="1beb2-216">, `docker run -it` <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, sırayla kapsayıcı durur.</span><span class="sxs-lookup"><span data-stu-id="1beb2-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="1beb2-217">`--rm` Parametre sağlandığından, işlem durdurulduğunda kapsayıcı otomatik olarak silinir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="1beb2-218">Var olmadığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="1beb2-218">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="1beb2-219">ENTRYPOINT'i değiştirme</span><span class="sxs-lookup"><span data-stu-id="1beb2-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="1beb2-220">Komut `docker run` ayrıca `ENTRYPOINT` *Dockerfile'deki* komutu değiştirmenize ve başka bir şey çalıştırmanıza olanak tanır, ancak yalnızca bu kapsayıcı için.</span><span class="sxs-lookup"><span data-stu-id="1beb2-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="1beb2-221">Örneğin, çalıştırmak `bash` için aşağıdaki komutu kullanın veya `cmd.exe`.</span><span class="sxs-lookup"><span data-stu-id="1beb2-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="1beb2-222">Komutu gerektiği gibi edin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="1beb2-223">Windows</span><span class="sxs-lookup"><span data-stu-id="1beb2-223">Windows</span></span>

<span data-ttu-id="1beb2-224">Bu örnekte, `ENTRYPOINT` '' olarak `cmd.exe`değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="1beb2-225"><kbd>CTRL</kbd>+<kbd>C</kbd> işlemi sona erdirmek ve kapsayıcı durdurmak için basılır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-225"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="1beb2-226">Linux</span><span class="sxs-lookup"><span data-stu-id="1beb2-226">Linux</span></span>

<span data-ttu-id="1beb2-227">Bu örnekte, `ENTRYPOINT` '' olarak `bash`değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="1beb2-228">İşlemi `quit` sona erdiren ve kapsayıcıyı durduran komut çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="1beb2-229">Temel komutlar</span><span class="sxs-lookup"><span data-stu-id="1beb2-229">Essential commands</span></span>

<span data-ttu-id="1beb2-230">Docker konteyner ve görüntüleri ile ne yapmak istediğinizi kapsayan birçok farklı komutları vardır.</span><span class="sxs-lookup"><span data-stu-id="1beb2-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="1beb2-231">Bu Docker komutları, kapsayıcılarınızı yönetmek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="1beb2-231">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="1beb2-232">docker build</span><span class="sxs-lookup"><span data-stu-id="1beb2-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="1beb2-233">docker çalıştırmak</span><span class="sxs-lookup"><span data-stu-id="1beb2-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="1beb2-234">docker ps</span><span class="sxs-lookup"><span data-stu-id="1beb2-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="1beb2-235">docker durağı</span><span class="sxs-lookup"><span data-stu-id="1beb2-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="1beb2-236">docker rm</span><span class="sxs-lookup"><span data-stu-id="1beb2-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="1beb2-237">docker rmi</span><span class="sxs-lookup"><span data-stu-id="1beb2-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="1beb2-238">docker görüntü</span><span class="sxs-lookup"><span data-stu-id="1beb2-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="1beb2-239">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="1beb2-239">Clean up resources</span></span>

<span data-ttu-id="1beb2-240">Bu öğretici sırasında, kapsayıcılar ve görüntüler oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="1beb2-240">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="1beb2-241">İstersenizin, bu kaynakları silin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-241">If you want, delete these resources.</span></span> <span data-ttu-id="1beb2-242">Aşağıdaki komutları kullanarak</span><span class="sxs-lookup"><span data-stu-id="1beb2-242">Use the following commands to</span></span>

01. <span data-ttu-id="1beb2-243">Tüm kapsayıcıları listele</span><span class="sxs-lookup"><span data-stu-id="1beb2-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="1beb2-244">Çalışan kapsayıcıları durdurun.</span><span class="sxs-lookup"><span data-stu-id="1beb2-244">Stop containers that are running.</span></span> <span data-ttu-id="1beb2-245">Kapsayıcıya `CONTAINER_NAME` otomatik olarak atanan adı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1beb2-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="1beb2-246">Kapsayıcıyı silme</span><span class="sxs-lookup"><span data-stu-id="1beb2-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="1beb2-247">Ardından, makinenizde artık istemediğiniz görüntüleri silin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="1beb2-248">*Dockerfile'Niz* tarafından oluşturulan görüntüyü silin ve ardından *Dockerfile'ın* temel inde olduğu .NET Core görüntüsünü silin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="1beb2-249">**IMAGE ID** veya **REPOSITORY:TAG** biçimlendirilmiş dizesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1beb2-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="1beb2-250">Yüklü `docker images` görüntülerin listesini görmek için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1beb2-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="1beb2-251">Resim dosyaları büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="1beb2-251">Image files can be large.</span></span> <span data-ttu-id="1beb2-252">Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="1beb2-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="1beb2-253">Genellikle, bu çalışma süresine bağlı olarak başka görüntüler oluşturmayı planlıyorsanız, temel görüntüleri çalışma zamanı yüklü olarak tutarsınız.</span><span class="sxs-lookup"><span data-stu-id="1beb2-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1beb2-254">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1beb2-254">Next steps</span></span>

- [<span data-ttu-id="1beb2-255">ASP.NET Core uygulamasını nasıl kaplaştırılamayı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-255">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="1beb2-256">Core Microservice Tutorial ASP.NET deneyin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-256">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="1beb2-257">Kapsayıcıları destekleyen Azure hizmetlerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-257">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="1beb2-258">Dockerfile komutları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="1beb2-258">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="1beb2-259">Visual Studio için Konteyner Araçlarını Keşfedin</span><span class="sxs-lookup"><span data-stu-id="1beb2-259">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)

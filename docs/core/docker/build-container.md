---
title: Docker öğreticisi ile uygulama Kapsayıcılı hale getirme
description: Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edineceksiniz.
ms.date: 01/09/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e1904430a591b0e74a69d50a53869a130fc0a248
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157836"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="0666f-103">Öğretici: bir .NET Core uygulamasını Kapsayıize edin</span><span class="sxs-lookup"><span data-stu-id="0666f-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="0666f-104">Bu öğretici, .NET Core uygulamanızı içeren bir Docker görüntüsü oluşturmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="0666f-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="0666f-105">Görüntü, yerel geliştirme ortamınız, özel bulut veya genel bulutunuz için kapsayıcılar oluşturmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0666f-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="0666f-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="0666f-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="0666f-107">Basit bir .NET Core uygulaması oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="0666f-107">Create and publish a simple .NET Core app</span></span>
> - <span data-ttu-id="0666f-108">.NET Core için Dockerfile oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0666f-108">Create and configure a Dockerfile for .NET Core</span></span>
> - <span data-ttu-id="0666f-109">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="0666f-109">Build a Docker image</span></span>
> - <span data-ttu-id="0666f-110">Docker kapsayıcısı oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0666f-110">Create and run a Docker container</span></span>

<span data-ttu-id="0666f-111">Docker kapsayıcısının bir .NET Core uygulaması için görevleri oluşturup dağıtduklarını anlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0666f-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="0666f-112">*Docker platformu* , uygulamaları *Docker görüntüleri*olarak hızlı bir şekilde oluşturmak ve paketlemek için *Docker altyapısını* kullanır.</span><span class="sxs-lookup"><span data-stu-id="0666f-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="0666f-113">Bu görüntüler, katmanlı bir kapsayıcıda dağıtılacak ve çalıştırılacak *Dockerfile* biçiminde yazılır.</span><span class="sxs-lookup"><span data-stu-id="0666f-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

> [!TIP]
> <span data-ttu-id="0666f-114">Mevcut bir ASP.NET Core uygulamasıyla çalışıyorsanız, [bir ASP.NET Core uygulama öğreticisini nasıl kapsayıtabilecek hakkında bilgi edinin](/aspnet/core/host-and-deploy/docker/building-net-docker-images) .</span><span class="sxs-lookup"><span data-stu-id="0666f-114">If you're working with an existing ASP.NET Core application, see the [Learn how to containerize an ASP.NET Core application](/aspnet/core/host-and-deploy/docker/building-net-docker-images) tutorial.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0666f-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0666f-115">Prerequisites</span></span>

<span data-ttu-id="0666f-116">Aşağıdaki önkoşulları yükler:</span><span class="sxs-lookup"><span data-stu-id="0666f-116">Install the following prerequisites:</span></span>

- <span data-ttu-id="0666f-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="0666f-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="0666f-118">.NET Core yüklüyse, kullanmakta olduğunuz SDK 'yı öğrenmek için `dotnet --info` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0666f-118">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

- [<span data-ttu-id="0666f-119">Docker Community sürümü</span><span class="sxs-lookup"><span data-stu-id="0666f-119">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

- <span data-ttu-id="0666f-120">*Dockerfile* ve .NET Core örnek uygulaması için geçici çalışma klasörü.</span><span class="sxs-lookup"><span data-stu-id="0666f-120">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="0666f-121">Bu öğreticide, *Docker-Working* adı çalışma klasörü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0666f-121">In this tutorial, the name *docker-working* is used as the working folder.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="0666f-122">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0666f-122">Create .NET Core app</span></span>

<span data-ttu-id="0666f-123">Docker kapsayıcısının çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="0666f-123">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="0666f-124">Terminalinizi açın, henüz yapmadıysanız bir çalışma klasörü oluşturun ve bunu girin.</span><span class="sxs-lookup"><span data-stu-id="0666f-124">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="0666f-125">Çalışma klasöründe, *uygulama*adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0666f-125">In the working folder, run the following command to create a new project in a subdirectory named *app*:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="0666f-126">Klasör ağaclarınız şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="0666f-126">Your folder tree will look like the following:</span></span>

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

<span data-ttu-id="0666f-127">`dotnet new` komutu, *uygulama* adlı yeni bir klasör oluşturur ve bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0666f-127">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="0666f-128">*Uygulama* klasörünü girin ve `dotnet run`komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0666f-128">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="0666f-129">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="0666f-129">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="0666f-130">Varsayılan şablon, terminale yazdıran ve ardından çıkış yapan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0666f-130">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="0666f-131">Bu öğretici için süresiz olarak döngü yapan bir uygulama kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0666f-131">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="0666f-132">*Program.cs* dosyasını bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="0666f-132">Open the *Program.cs* file in a text editor.</span></span> <span data-ttu-id="0666f-133">Şu anda şu kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="0666f-133">It should currently look like the following code:</span></span>

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

<span data-ttu-id="0666f-134">Dosyayı her saniye sayı sayan aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0666f-134">Replace the file with the following code that counts numbers every second:</span></span>

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

<span data-ttu-id="0666f-135">Dosyayı kaydedin ve `dotnet run`programı yeniden test edin.</span><span class="sxs-lookup"><span data-stu-id="0666f-135">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="0666f-136">Bu uygulamanın süresiz olarak çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0666f-136">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="0666f-137">Durdurmak için <kbd>CTRL</kbd>+, Cancel <kbd></kbd> komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0666f-137">Use the cancel command <kbd>CTRL</kbd>+<kbd>C</kbd> to stop it.</span></span> <span data-ttu-id="0666f-138">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="0666f-138">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="0666f-139">Uygulama için komut satırına bir sayı geçirirseniz, bu miktarı yalnızca bu miktara göre sayılır ve ardından çıkış olur.</span><span class="sxs-lookup"><span data-stu-id="0666f-139">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="0666f-140">Beş ile saymak için `dotnet run -- 5` deneyin.</span><span class="sxs-lookup"><span data-stu-id="0666f-140">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="0666f-141">`--` sonraki parametreler `dotnet run` komutuna geçirilmez ve bunun yerine uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="0666f-141">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="0666f-142">.NET Core uygulaması Yayımla</span><span class="sxs-lookup"><span data-stu-id="0666f-142">Publish .NET Core app</span></span>

<span data-ttu-id="0666f-143">.NET Core uygulamanızı Docker görüntüsüne eklemeden önce yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="0666f-143">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="0666f-144">Kapsayıcının, başlatıldığında uygulamanın yayımlanmış sürümünü çalıştırmasını sağlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="0666f-144">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="0666f-145">Çalışma klasöründen, örnek kaynak kodu ile *uygulama* klasörünü girin ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0666f-145">From the working folder, enter the *app* folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="0666f-146">Bu komut, uygulamanızı *Yayımla* klasörüne derler.</span><span class="sxs-lookup"><span data-stu-id="0666f-146">This command compiles your app to the *publish* folder.</span></span> <span data-ttu-id="0666f-147">Çalışma klasöründeki *Yayımla* klasörünün yolu `.\app\bin\Release\netcoreapp3.1\publish\` olmalıdır</span><span class="sxs-lookup"><span data-stu-id="0666f-147">The path to the *publish* folder from the working folder should be `.\app\bin\Release\netcoreapp3.1\publish\`</span></span>

<span data-ttu-id="0666f-148">*App* klasöründen, *MyApp. dll* dosyasının oluşturulduğunu doğrulamak için Yayımla klasörünün bir dizin listesini alın.</span><span class="sxs-lookup"><span data-stu-id="0666f-148">From the *app* folder, get a directory listing of the publish folder to verify that the *myapp.dll* file was created.</span></span>

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

<span data-ttu-id="0666f-149">Linux veya macOS kullanıyorsanız, dizin listesi almak için `ls` komutunu kullanın ve *MyApp. dll* dosyasının oluşturulduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="0666f-149">If you're using Linux or macOS, use the `ls` command to get a directory listing and verify that the *myapp.dll* file was created.</span></span>

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="0666f-150">Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="0666f-150">Create the Dockerfile</span></span>

<span data-ttu-id="0666f-151">*Dockerfile* dosyası `docker build` komutu tarafından bir kapsayıcı görüntüsü oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0666f-151">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="0666f-152">Bu dosya, uzantısı olmayan *Dockerfile* adlı bir metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0666f-152">This file is a text file named *Dockerfile* that doesn't have an extension.</span></span>

<span data-ttu-id="0666f-153">Terminalinizde, başlangıçta oluşturduğunuz çalışma klasörünün dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="0666f-153">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="0666f-154">Çalışma klasörünüzde *Dockerfile* adlı bir dosya oluşturun ve dosyayı bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="0666f-154">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="0666f-155">Kapsayıcılı olduğunuz uygulamanın türüne bağlı olarak, ASP.NET Core çalışma zamanını veya .NET Core çalışma zamanını seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="0666f-155">Depending on the type of application you're going to containerize, you'll choose either the ASP.NET Core runtime or the .NET Core runtime.</span></span> <span data-ttu-id="0666f-156">Şüpheli olduğunda, .NET Core çalışma zamanını içeren ASP.NET Core çalışma zamanını seçin.</span><span class="sxs-lookup"><span data-stu-id="0666f-156">When in doubt, choose the ASP.NET Core runtime, which includes the .NET Core runtime.</span></span> <span data-ttu-id="0666f-157">Bu öğretici ASP.NET Core çalışma zamanı görüntüsünü kullanır, ancak önceki bölümlerde oluşturulan uygulama bir .NET Core uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="0666f-157">This tutorial will use the ASP.NET Core runtime image, but the application created in the previous sections is an .NET Core application.</span></span>

- <span data-ttu-id="0666f-158">ASP.NET Core çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="0666f-158">ASP.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
  ```

- <span data-ttu-id="0666f-159">.NET core çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="0666f-159">.NET Core runtime</span></span>

  ```dockerfile
  FROM mcr.microsoft.com/dotnet/core/runtime:3.1
  ```

<span data-ttu-id="0666f-160">`FROM` komutu, Docker 'ın belirtilen depodan etiketlenen **3,1** görüntüsünü çekmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="0666f-160">The `FROM` command tells Docker to pull down the image tagged **3.1** from the specified repository.</span></span> <span data-ttu-id="0666f-161">SDK 'nizin hedeflediği çalışma zamanıyla eşleşen çalışma zamanı sürümünü çekdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0666f-161">Make sure that you pull the runtime version that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="0666f-162">Örneğin, önceki bölümde oluşturulan uygulama .NET Core 3,1 SDK 'sını ve *Dockerfile* içinde başvurulan temel görüntüyü **3,1**ile etiketledi.</span><span class="sxs-lookup"><span data-stu-id="0666f-162">For example, the app created in the previous section used the .NET Core 3.1 SDK and the base image referred to in the *Dockerfile* is tagged with **3.1**.</span></span>

<span data-ttu-id="0666f-163">*Dockerfile* dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="0666f-163">Save the *Dockerfile* file.</span></span> <span data-ttu-id="0666f-164">Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="0666f-164">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="0666f-165">Daha derin düzey dosya ve klasörlerin bazıları, makalede yer kazanmak için kesildi:</span><span class="sxs-lookup"><span data-stu-id="0666f-165">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

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

<span data-ttu-id="0666f-166">Terminalinizden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0666f-166">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="0666f-167">Docker, *Dockerfile*dosyasındaki her satırı işleyecek.</span><span class="sxs-lookup"><span data-stu-id="0666f-167">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="0666f-168">`docker build` komutundaki `.`, Docker 'ın bir *Dockerfile*bulmak için geçerli klasörü kullanmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="0666f-168">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="0666f-169">Bu komut, görüntüyü oluşturur ve bu görüntüyü işaret eden **MyImage** adlı bir yerel depo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0666f-169">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="0666f-170">Bu komut bittikten sonra, yüklenen görüntülerin listesini görmek için `docker images` çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0666f-170">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              38db0eb8f648        4 weeks ago         346MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 38db0eb8f648        4 weeks ago         346MB
```

<span data-ttu-id="0666f-171">İki görüntünün aynı **görüntü kimliği** değerini paylaştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="0666f-171">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="0666f-172">*Dockerfile* 'daki tek komut yeni görüntünün varolan bir görüntüye dayandırdığı için, her iki görüntü arasında değer aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0666f-172">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="0666f-173">*Dockerfile dosyasına*iki komut ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="0666f-173">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="0666f-174">Her komut, **MyImage** Repository girişinin işaret ettiği görüntüyü temsil eden son komutla yeni bir görüntü katmanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0666f-174">Each command creates a new image layer with the final command representing the image the **myimage** repository entry points to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp3.1/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="0666f-175">`COPY` komutu, Docker 'a bilgisayarınızdaki belirtilen klasörü kapsayıcıda bir klasöre kopyalamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="0666f-175">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="0666f-176">Bu örnekte, *Publish* klasörü kapsayıcıda *uygulama* adlı bir klasöre kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="0666f-176">In this example, the *publish* folder is copied to a folder named *app* in the container.</span></span>

<span data-ttu-id="0666f-177">`ENTRYPOINT`sonraki komut, Docker 'ın kapsayıcıyı yürütülebilir olarak çalışacak şekilde yapılandırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="0666f-177">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="0666f-178">Kapsayıcı başladığında `ENTRYPOINT` komutu çalışır.</span><span class="sxs-lookup"><span data-stu-id="0666f-178">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="0666f-179">Bu komut sona erdiğinde kapsayıcı otomatik olarak durur.</span><span class="sxs-lookup"><span data-stu-id="0666f-179">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="0666f-180">Terminalinizden `docker build -t myimage -f Dockerfile .` çalıştırın ve bu komutun ne zaman tamamlanerdiğinde `docker images`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0666f-180">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

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

<span data-ttu-id="0666f-181">*Dockerfile* 'daki her komut bir katman oluşturdu ve BIR **görüntü kimliği**oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="0666f-181">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="0666f-182">Son **görüntü kimliği** (sizinki farklı olacak) **ddcc6646461b** ve bir sonraki adımda bu görüntüye göre bir kapsayıcı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="0666f-182">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="0666f-183">Bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0666f-183">Create a container</span></span>

<span data-ttu-id="0666f-184">Artık uygulamanızı içeren bir görüntünüz olduğuna göre, bir kapsayıcı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0666f-184">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="0666f-185">Bir kapsayıcıyı iki şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0666f-185">You can create a container in two ways.</span></span> <span data-ttu-id="0666f-186">İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0666f-186">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
ceda87b219a4e55e9ad5d833ee1a7ea4da21b5ea7ce5a7d08f3051152e784944
```

<span data-ttu-id="0666f-187">Yukarıdaki `docker create` komutu, **MyImage** görüntüsünü temel alan bir kapsayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0666f-187">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="0666f-188">Bu komutun çıktısı, oluşturulan kapsayıcının **KAPSAYıCı kimliğini** (sizinki farklı olacak) gösterir.</span><span class="sxs-lookup"><span data-stu-id="0666f-188">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="0666f-189">*Tüm* kapsayıcıların listesini görmek için `docker ps -a` komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0666f-189">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               gallant_lehmann
```

### <a name="manage-the-container"></a><span data-ttu-id="0666f-190">Kapsayıcıyı yönetme</span><span class="sxs-lookup"><span data-stu-id="0666f-190">Manage the container</span></span>

<span data-ttu-id="0666f-191">Her kapsayıcıya, bu kapsayıcı örneğine başvurmak için kullanabileceğiniz bir rastgele ad atanır.</span><span class="sxs-lookup"><span data-stu-id="0666f-191">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="0666f-192">Örneğin, otomatik olarak oluşturulan kapsayıcı **gallant_lehmann** adı (sizinki farklı olacaktır) seçti ve bu ad kapsayıcıyı başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0666f-192">For example, the container that was created automatically chose the name **gallant_lehmann** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="0666f-193">Otomatik adı, `docker create --name` parametresini kullanarak belirli bir adla geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0666f-193">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="0666f-194">Aşağıdaki örnek, kapsayıcıyı başlatmak için `docker start` komutunu kullanır ve sonra yalnızca çalıştıran kapsayıcıları göstermek için `docker ps` komutunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="0666f-194">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           gallant_lehmann
```

<span data-ttu-id="0666f-195">Benzer şekilde, `docker stop` komutu kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="0666f-195">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="0666f-196">Aşağıdaki örnek, kapsayıcıyı durdurmak için `docker stop` komutunu kullanır ve ardından hiçbir kapsayıcının çalışmadığını göstermek için `docker ps` komutunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="0666f-196">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running:</span></span>

```console
> docker stop gallant_lehmann
gallant_lehmann

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="0666f-197">Bir kapsayıcıya bağlanma</span><span class="sxs-lookup"><span data-stu-id="0666f-197">Connect to a container</span></span>

<span data-ttu-id="0666f-198">Bir kapsayıcı çalışmaya başladıktan sonra çıktıyı görmek için bu sunucuya bağlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0666f-198">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="0666f-199">Kapsayıcıyı başlatmak ve çıkış akışına gözatmak için `docker start` ve `docker attach` komutlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0666f-199">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="0666f-200">Bu örnekte, <kbd>CTRL + C</kbd> tuş vuruşu, çalışan kapsayıcıyı ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0666f-200">In this example, the <kbd>CTRL + C</kbd> keystroke is used to detach from the running container.</span></span> <span data-ttu-id="0666f-201">Bu tuş vuruşu, kapsayıcıyı durduran kapsayıcıyı gerçekten sonlandırarak işlemden çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="0666f-201">This keystroke may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="0666f-202">`--sig-proxy=false` parametresi, <kbd>CTRL + C</kbd> 'nin kapsayıcıdaki işlemi durdurmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0666f-202">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="0666f-203">Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saymakta olduğunu doğrulamak için yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="0666f-203">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

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

### <a name="delete-a-container"></a><span data-ttu-id="0666f-204">Kapsayıcı silme</span><span class="sxs-lookup"><span data-stu-id="0666f-204">Delete a container</span></span>

<span data-ttu-id="0666f-205">Bu makalenin amaçları doğrultusunda, kapsayıcıların hiçbir şey yapmadan asılı istememeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0666f-205">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="0666f-206">Daha önce oluşturduğunuz kapsayıcıyı silin.</span><span class="sxs-lookup"><span data-stu-id="0666f-206">Delete the container you previously created.</span></span> <span data-ttu-id="0666f-207">Kapsayıcı çalışıyorsa durdurun.</span><span class="sxs-lookup"><span data-stu-id="0666f-207">If the container is running, stop it.</span></span>

```console
> docker stop gallant_lehmann
```

<span data-ttu-id="0666f-208">Aşağıdaki örnekte tüm kapsayıcılar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0666f-208">The following example lists all containers.</span></span> <span data-ttu-id="0666f-209">Ardından, kapsayıcıyı silmek için `docker rm` komutunu kullanır ve ardından çalışan kapsayıcılar için ikinci bir kez kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="0666f-209">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
ceda87b219a4        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             gallant_lehmann

> docker rm gallant_lehmann
gallant_lehmann

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="0666f-210">Tek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0666f-210">Single run</span></span>

<span data-ttu-id="0666f-211">Docker, kapsayıcıyı tek bir komut olarak oluşturup çalıştırmak için `docker run` komutu sağlar.</span><span class="sxs-lookup"><span data-stu-id="0666f-211">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="0666f-212">Bu komut `docker create` çalıştırma gereksinimini ortadan kaldırır ve `docker start`.</span><span class="sxs-lookup"><span data-stu-id="0666f-212">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="0666f-213">Kapsayıcı durdurulduğunda kapsayıcıyı otomatik olarak silmek için de bu komutu ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0666f-213">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="0666f-214">Örneğin, iki şeyi yapmak için `docker run -it --rm` kullanın, ilk olarak kapsayıcıya bağlanmak için geçerli terminali otomatik olarak kullanın ve ardından kapsayıcı tamamlandığında onu kaldırın:</span><span class="sxs-lookup"><span data-stu-id="0666f-214">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="0666f-215">`docker run -it`, <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, bu da kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="0666f-215">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="0666f-216">`--rm` parametresi sağlandığından, işlem durdurulduğunda kapsayıcı otomatik olarak silinir.</span><span class="sxs-lookup"><span data-stu-id="0666f-216">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="0666f-217">Mevcut olmadığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="0666f-217">Verify that it doesn't exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="0666f-218">GIRIŞ noktasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="0666f-218">Change the ENTRYPOINT</span></span>

<span data-ttu-id="0666f-219">`docker run` komutu aynı zamanda *Dockerfile* içindeki `ENTRYPOINT` komutunu değiştirmenize ve yalnızca bu kapsayıcı için başka bir şey çalıştırmanıza imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="0666f-219">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="0666f-220">Örneğin, `bash` veya `cmd.exe`çalıştırmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0666f-220">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="0666f-221">Komutu gereken şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="0666f-221">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="0666f-222">Windows</span><span class="sxs-lookup"><span data-stu-id="0666f-222">Windows</span></span>

<span data-ttu-id="0666f-223">Bu örnekte, `ENTRYPOINT` `cmd.exe`olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="0666f-223">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="0666f-224">İşlemi sonlandırmak ve kapsayıcıyı durdurmak için <kbd>CTRL</kbd>+<kbd>C</kbd> 'ye basıldığında.</span><span class="sxs-lookup"><span data-stu-id="0666f-224"><kbd>CTRL</kbd>+<kbd>C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="0666f-225">Linux</span><span class="sxs-lookup"><span data-stu-id="0666f-225">Linux</span></span>

<span data-ttu-id="0666f-226">Bu örnekte, `ENTRYPOINT` `bash`olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="0666f-226">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="0666f-227">`quit` komutu işlemi sonlandırır ve kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="0666f-227">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="0666f-228">Gerekli komutlar</span><span class="sxs-lookup"><span data-stu-id="0666f-228">Essential commands</span></span>

<span data-ttu-id="0666f-229">Docker, kapsayıcınıza ve görüntülerinize ne yapmak istediğinizi kapsayan birçok farklı komuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0666f-229">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="0666f-230">Bu Docker komutları, Kapsayıcılarınızı yönetmek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="0666f-230">These Docker commands are essential to managing your containers:</span></span>

- [<span data-ttu-id="0666f-231">Docker derlemesi</span><span class="sxs-lookup"><span data-stu-id="0666f-231">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
- [<span data-ttu-id="0666f-232">Docker çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0666f-232">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
- [<span data-ttu-id="0666f-233">Docker PS</span><span class="sxs-lookup"><span data-stu-id="0666f-233">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
- [<span data-ttu-id="0666f-234">Docker durdur</span><span class="sxs-lookup"><span data-stu-id="0666f-234">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
- [<span data-ttu-id="0666f-235">Docker RM</span><span class="sxs-lookup"><span data-stu-id="0666f-235">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
- [<span data-ttu-id="0666f-236">Docker rmi</span><span class="sxs-lookup"><span data-stu-id="0666f-236">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
- [<span data-ttu-id="0666f-237">Docker görüntüsü</span><span class="sxs-lookup"><span data-stu-id="0666f-237">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="0666f-238">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="0666f-238">Clean up resources</span></span>

<span data-ttu-id="0666f-239">Bu öğreticide kapsayıcılar ve görüntüler oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="0666f-239">During this tutorial, you created containers and images.</span></span> <span data-ttu-id="0666f-240">İsterseniz, bu kaynakları silin.</span><span class="sxs-lookup"><span data-stu-id="0666f-240">If you want, delete these resources.</span></span> <span data-ttu-id="0666f-241">İçin aşağıdaki komutları kullanın</span><span class="sxs-lookup"><span data-stu-id="0666f-241">Use the following commands to</span></span>

01. <span data-ttu-id="0666f-242">Tüm kapsayıcıları Listele</span><span class="sxs-lookup"><span data-stu-id="0666f-242">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="0666f-243">Çalıştıran kapsayıcıları durdurun.</span><span class="sxs-lookup"><span data-stu-id="0666f-243">Stop containers that are running.</span></span> <span data-ttu-id="0666f-244">`CONTAINER_NAME`, kapsayıcıya otomatik olarak atanan adı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0666f-244">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="0666f-245">Kapsayıcıyı silme</span><span class="sxs-lookup"><span data-stu-id="0666f-245">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="0666f-246">Sonra, makinenizde artık istemediğiniz görüntüleri silin.</span><span class="sxs-lookup"><span data-stu-id="0666f-246">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="0666f-247">*Dockerfile* dosyanız tarafından oluşturulan görüntüyü silin ve ardından *dockerfile* ' ın dayandığı .NET Core görüntüsünü silin.</span><span class="sxs-lookup"><span data-stu-id="0666f-247">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="0666f-248">**Görüntü kimliğini** veya **Depo: etiketli dize etiketini** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0666f-248">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

<span data-ttu-id="0666f-249">Yüklenen görüntülerin listesini görmek için `docker images` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="0666f-249">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="0666f-250">Görüntü dosyaları büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="0666f-250">Image files can be large.</span></span> <span data-ttu-id="0666f-251">Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="0666f-251">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="0666f-252">Bu çalışma zamanına göre diğer görüntüleri oluşturmayı planlıyorsanız, genellikle temel görüntüleri çalışma zamanı yüklü olarak tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0666f-252">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0666f-253">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0666f-253">Next steps</span></span>

- [<span data-ttu-id="0666f-254">ASP.NET Core uygulamasını kapsayıya kapsayıtabilecek hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="0666f-254">Learn how to containerize an ASP.NET Core application.</span></span>](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [<span data-ttu-id="0666f-255">ASP.NET Core mikro hizmet öğreticisini deneyin.</span><span class="sxs-lookup"><span data-stu-id="0666f-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
- [<span data-ttu-id="0666f-256">Kapsayıcıları destekleyen Azure hizmetlerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="0666f-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
- [<span data-ttu-id="0666f-257">Dockerfile komutları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="0666f-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
- [<span data-ttu-id="0666f-258">Visual Studio için kapsayıcı araçlarını keşfet</span><span class="sxs-lookup"><span data-stu-id="0666f-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)

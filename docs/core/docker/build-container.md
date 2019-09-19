---
title: Docker öğreticisi ile uygulama Kapsayıcılı hale getirme
description: Bu öğreticide, Docker ile bir .NET Core uygulamasını kapsayıya kapsayıtabilecek öğreneceksiniz.
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 5e05fd2a38770ce348fbbfcfaa88267217b806bf
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116564"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="a8242-103">Öğretici: .NET Core uygulamasını kapsayıcılı hale getirme</span><span class="sxs-lookup"><span data-stu-id="a8242-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="a8242-104">Bu öğretici, .NET Core uygulamanızı içeren bir Docker görüntüsü oluşturmayı öğretir.</span><span class="sxs-lookup"><span data-stu-id="a8242-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="a8242-105">Görüntü, yerel geliştirme ortamınız, özel bulut veya genel bulutunuz için kapsayıcılar oluşturmak üzere kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8242-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="a8242-106">Şunları öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="a8242-106">You'll learn to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="a8242-107">Basit bir .NET Core uygulaması oluşturma ve yayımlama</span><span class="sxs-lookup"><span data-stu-id="a8242-107">Create and publish a simple .NET Core app</span></span>
> * <span data-ttu-id="a8242-108">.NET Core için Dockerfile oluşturma ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a8242-108">Create and configure a Dockerfile for .NET Core</span></span>
> * <span data-ttu-id="a8242-109">Docker görüntüsü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8242-109">Build a Docker image</span></span>
> * <span data-ttu-id="a8242-110">Docker kapsayıcısı oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a8242-110">Create and run a Docker container</span></span>

<span data-ttu-id="a8242-111">Docker kapsayıcısının bir .NET Core uygulaması için görevleri oluşturup dağıtduklarını anlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a8242-111">You'll understand the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="a8242-112">*Docker platformu* , uygulamaları *Docker görüntüleri*olarak hızlı bir şekilde oluşturmak ve paketlemek için *Docker altyapısını* kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8242-112">The *Docker platform* uses the *Docker engine* to quickly build and package apps as *Docker images*.</span></span> <span data-ttu-id="a8242-113">Bu görüntüler, katmanlı bir kapsayıcıda dağıtılacak ve çalıştırılacak *Dockerfile* biçiminde yazılır.</span><span class="sxs-lookup"><span data-stu-id="a8242-113">These images are written in the *Dockerfile* format to be deployed and run in a layered container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a8242-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a8242-114">Prerequisites</span></span>

<span data-ttu-id="a8242-115">Aşağıdaki önkoşulları yükler:</span><span class="sxs-lookup"><span data-stu-id="a8242-115">Install the following prerequisites:</span></span>

* <span data-ttu-id="a8242-116">[.NET Core 2,2 SDK](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="a8242-116">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)</span></span>\
<span data-ttu-id="a8242-117">.NET Core yüklüyse, kullanmakta olduğunuz SDK 'yı öğrenmek `dotnet --info` için komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8242-117">If you have .NET Core installed, use the `dotnet --info` command to determine which SDK you're using.</span></span>

* [<span data-ttu-id="a8242-118">Docker Community sürümü</span><span class="sxs-lookup"><span data-stu-id="a8242-118">Docker Community Edition</span></span>](https://www.docker.com/products/docker-desktop)

* <span data-ttu-id="a8242-119">*Dockerfile* ve .NET Core örnek uygulaması için geçici çalışma klasörü.</span><span class="sxs-lookup"><span data-stu-id="a8242-119">A temporary working folder for the *Dockerfile* and .NET Core example app.</span></span> <span data-ttu-id="a8242-120">Bu öğreticide, ad `docker-working` çalışma klasörü olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8242-120">In this tutorial, the name `docker-working` is used as the working folder.</span></span>

### <a name="use-sdk-version-22"></a><span data-ttu-id="a8242-121">SDK sürüm 2,2 kullanma</span><span class="sxs-lookup"><span data-stu-id="a8242-121">Use SDK version 2.2</span></span>

<span data-ttu-id="a8242-122">3,0 gibi daha yeni bir SDK kullanıyorsanız uygulamanızın 2,2 SDK 'Yı kullanmaya zorlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8242-122">If you're using an SDK that is newer, like 3.0, make sure that your app is forced to use the 2.2 SDK.</span></span> <span data-ttu-id="a8242-123">Çalışma klasörünüzde adlı `global.json` bir dosya oluşturun ve aşağıdaki JSON kodunu yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="a8242-123">Create a file named `global.json` in your working folder and paste in the following json code:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

<span data-ttu-id="a8242-124">Bu dosyayı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a8242-124">Save this file.</span></span> <span data-ttu-id="a8242-125">Dosya varlığı, .NET Core 'un bu klasörden ve aşağıda çağrılan herhangi bir `dotnet` komut için sürüm 2,2 ' i kullanmasına zorlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="a8242-125">The presence of file will force .NET Core to use version 2.2 for any `dotnet` command called from this folder and below.</span></span>

## <a name="create-net-core-app"></a><span data-ttu-id="a8242-126">.NET Core uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8242-126">Create .NET Core app</span></span>

<span data-ttu-id="a8242-127">Docker kapsayıcısının çalışacağı bir .NET Core uygulamasına ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="a8242-127">You need a .NET Core app that the Docker container will run.</span></span> <span data-ttu-id="a8242-128">Terminalinizi açın, henüz yapmadıysanız bir çalışma klasörü oluşturun ve bunu girin.</span><span class="sxs-lookup"><span data-stu-id="a8242-128">Open your terminal, create a working folder if you haven't already, and enter it.</span></span> <span data-ttu-id="a8242-129">Çalışma klasöründe, uygulama adlı bir alt dizinde yeni bir proje oluşturmak için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a8242-129">In the working folder, run the following command to create a new project in a subdirectory named app:</span></span>

```dotnetcli
dotnet new console -o app -n myapp
```

<span data-ttu-id="a8242-130">Klasör ağaclarınız şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="a8242-130">Your folder tree will look like the following:</span></span>

```
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

<span data-ttu-id="a8242-131">Komut `dotnet new` , *uygulama* adlı yeni bir klasör oluşturur ve bir "Merhaba Dünya" uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8242-131">The `dotnet new` command creates a new folder named *app* and generates a "Hello World" app.</span></span> <span data-ttu-id="a8242-132">*Uygulama* klasörünü girip komutunu `dotnet run`çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a8242-132">Enter the *app* folder and run the command `dotnet run`.</span></span> <span data-ttu-id="a8242-133">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="a8242-133">You'll see the following output:</span></span>

```console
> dotnet run
Hello World!
```

<span data-ttu-id="a8242-134">Varsayılan şablon, terminale yazdıran ve ardından çıkış yapan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8242-134">The default template creates an app that prints to the terminal and then exits.</span></span> <span data-ttu-id="a8242-135">Bu öğretici için süresiz olarak döngü yapan bir uygulama kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a8242-135">For this tutorial, you'll use an app that loops indefinitely.</span></span> <span data-ttu-id="a8242-136">**Program.cs** dosyasını bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="a8242-136">Open the **Program.cs** file in a text editor.</span></span> <span data-ttu-id="a8242-137">Şu anda şu kod gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="a8242-137">It should currently look like the following code:</span></span>

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

<span data-ttu-id="a8242-138">Dosyayı her saniye sayı sayan aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a8242-138">Replace the file with the following code that counts numbers every second:</span></span>

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
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

<span data-ttu-id="a8242-139">Dosyayı kaydedin ve ile `dotnet run`programı test edin.</span><span class="sxs-lookup"><span data-stu-id="a8242-139">Save the file and test the program again with `dotnet run`.</span></span> <span data-ttu-id="a8242-140">Bu uygulamanın süresiz olarak çalıştığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a8242-140">Remember that this app runs indefinitely.</span></span> <span data-ttu-id="a8242-141">Durdurmak için <kbd>CTRL + C</kbd> Cancel komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8242-141">Use the cancel command <kbd>CTRL + C</kbd> to stop it.</span></span> <span data-ttu-id="a8242-142">Aşağıdaki çıktıyı görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="a8242-142">You'll see the following output:</span></span>

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

<span data-ttu-id="a8242-143">Uygulama için komut satırına bir sayı geçirirseniz, bu miktarı yalnızca bu miktara göre sayılır ve ardından çıkış olur.</span><span class="sxs-lookup"><span data-stu-id="a8242-143">If you pass a number on the command line to the app, it will only count up to that amount and then exit.</span></span> <span data-ttu-id="a8242-144">Beş olarak saymak için deneyin. `dotnet run -- 5`</span><span class="sxs-lookup"><span data-stu-id="a8242-144">Try it with `dotnet run -- 5` to count to five.</span></span>

> [!NOTE]
> <span data-ttu-id="a8242-145">Sonrasında `--` herhangi bir parametre `dotnet run` komutuna geçirilmez ve bunun yerine uygulamanıza geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a8242-145">Any parameters after `--` are not passed to the `dotnet run` command and instead are passed to your application.</span></span>

## <a name="publish-net-core-app"></a><span data-ttu-id="a8242-146">.NET Core uygulaması Yayımla</span><span class="sxs-lookup"><span data-stu-id="a8242-146">Publish .NET Core app</span></span>

<span data-ttu-id="a8242-147">.NET Core uygulamanızı Docker görüntüsüne eklemeden önce yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="a8242-147">Before you add your .NET Core app to the Docker image, publish it.</span></span> <span data-ttu-id="a8242-148">Kapsayıcının, başlatıldığında uygulamanın yayımlanmış sürümünü çalıştırmasını sağlamak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a8242-148">You want to make sure that the container runs the published version of the app when it's started.</span></span>

<span data-ttu-id="a8242-149">Çalışma klasöründen, örnek kaynak kodu ile **uygulama** klasörünü girin ve şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a8242-149">From the working folder, enter the **app** folder with the example source code and run the following command:</span></span>

```dotnetcli
dotnet publish -c Release
```

<span data-ttu-id="a8242-150">Bu komut, uygulamanızı **Yayımla** klasörüne derler.</span><span class="sxs-lookup"><span data-stu-id="a8242-150">This command compiles your app to the **publish** folder.</span></span> <span data-ttu-id="a8242-151">Çalışma klasöründeki **Yayımla** klasörünün yolu`.\app\bin\Release\netcoreapp2.2\publish\`</span><span class="sxs-lookup"><span data-stu-id="a8242-151">The path to the **publish** folder from the working folder should be `.\app\bin\Release\netcoreapp2.2\publish\`</span></span>

<span data-ttu-id="a8242-152">**MyApp. dll** dosyasının oluşturulduğunu doğrulamak için Yayımla klasörünün bir dizin listesini alın.</span><span class="sxs-lookup"><span data-stu-id="a8242-152">Get a directory listing of the publish folder to verify that the **myapp.dll** was created.</span></span> <span data-ttu-id="a8242-153">**Uygulama** klasöründen aşağıdaki komutlardan birini çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a8242-153">From the **app** folder, run one of the following commands:</span></span>

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a><span data-ttu-id="a8242-154">Dockerfile oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8242-154">Create the Dockerfile</span></span>

<span data-ttu-id="a8242-155">*Dockerfile* dosyası `docker build` komut tarafından bir kapsayıcı görüntüsü oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8242-155">The *Dockerfile* file is used by the `docker build` command to create a container image.</span></span> <span data-ttu-id="a8242-156">Bu dosya, uzantısı olmayan *Dockerfile* adlı bir düz metin dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a8242-156">This file is a plaintext file named *Dockerfile* that does not have an extension.</span></span>

<span data-ttu-id="a8242-157">Terminalinizde, başlangıçta oluşturduğunuz çalışma klasörünün dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="a8242-157">In your terminal, navigate up a directory to the working folder you created at the start.</span></span> <span data-ttu-id="a8242-158">Çalışma klasörünüzde *Dockerfile* adlı bir dosya oluşturun ve dosyayı bir metin düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="a8242-158">Create a file named *Dockerfile* in your working folder and open it in a text editor.</span></span> <span data-ttu-id="a8242-159">Aşağıdaki komutu dosyanın ilk satırı olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a8242-159">Add the following command as the first line of the file:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="a8242-160">Komut `FROM` , Docker 'ın **MCR.Microsoft.com/DotNet/Core/Runtime** deposundan etiketli **2,2** görüntüsünü çekmesini söyler.</span><span class="sxs-lookup"><span data-stu-id="a8242-160">The `FROM` command tells Docker to pull down the image tagged **2.2** from the **mcr.microsoft.com/dotnet/core/runtime** repository.</span></span> <span data-ttu-id="a8242-161">SDK 'nizin hedeflediği çalışma zamanına uyan .NET Core çalışma zamanını çekdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8242-161">Make sure that you pull the .NET Core runtime that matches the runtime targeted by your SDK.</span></span> <span data-ttu-id="a8242-162">Örneğin, önceki bölümde oluşturulan uygulama .NET Core 2,2 SDK 'sını kullandı ve .NET Core 2,2 ' yi hedefleyen bir uygulama oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="a8242-162">For example, the app created in the previous section used the .NET Core 2.2 SDK and created an app that targeted .NET Core 2.2.</span></span> <span data-ttu-id="a8242-163">Bu nedenle, *Dockerfile* dosyasında başvurulan temel görüntü **2,2**ile etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="a8242-163">So the base image referred to in the *Dockerfile* is tagged with **2.2**.</span></span>

<span data-ttu-id="a8242-164">*Dockerfile* dosyasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a8242-164">Save the *Dockerfile* file.</span></span> <span data-ttu-id="a8242-165">Çalışma klasörünün dizin yapısı aşağıdaki gibi görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="a8242-165">The directory structure of the working folder should look like the following.</span></span> <span data-ttu-id="a8242-166">Daha derin düzey dosya ve klasörlerin bazıları, makalede yer kazanmak için kesildi:</span><span class="sxs-lookup"><span data-stu-id="a8242-166">Some of the deeper-level files and folders have been cut to save space in the article:</span></span>

```
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

<span data-ttu-id="a8242-167">Terminalinizden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a8242-167">From your terminal, run the following command:</span></span>

```console
docker build -t myimage -f Dockerfile .
```

<span data-ttu-id="a8242-168">Docker, *Dockerfile*dosyasındaki her satırı işleyecek.</span><span class="sxs-lookup"><span data-stu-id="a8242-168">Docker will process each line in the *Dockerfile*.</span></span> <span data-ttu-id="a8242-169">Komutunda Docker 'ın bir *dockerfile dosyasını*bulmak için geçerli klasörü kullanmasını söyler. `.` `docker build`</span><span class="sxs-lookup"><span data-stu-id="a8242-169">The `.` in the `docker build` command tells Docker to use the current folder to find a *Dockerfile*.</span></span> <span data-ttu-id="a8242-170">Bu komut, görüntüyü oluşturur ve bu görüntüyü işaret eden **MyImage** adlı bir yerel depo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8242-170">This command builds the image and creates a local repository named **myimage** that points to that image.</span></span> <span data-ttu-id="a8242-171">Bu komut tamamlandıktan sonra, yüklenen `docker images` görüntülerin listesini görmek için komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="a8242-171">After this command finishes, run `docker images` to see a list of images installed:</span></span>

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="a8242-172">İki görüntünün aynı **görüntü kimliği** değerini paylaştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8242-172">Notice that the two images share the same **IMAGE ID** value.</span></span> <span data-ttu-id="a8242-173">*Dockerfile* 'daki tek komut yeni görüntünün varolan bir görüntüye dayandırdığı için, her iki görüntü arasında değer aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a8242-173">The value is the same between both images because the only command in the *Dockerfile* was to base the new image on an existing image.</span></span> <span data-ttu-id="a8242-174">*Dockerfile dosyasına*iki komut ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="a8242-174">Let's add two commands to the *Dockerfile*.</span></span> <span data-ttu-id="a8242-175">Her komut, **MyImage** deposunun işaret ettiği görüntüyü temsil eden son komutla yeni bir görüntü katmanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a8242-175">Each command creates a new image layer with the final command representing the image the **myimage** repository will point to.</span></span>

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

<span data-ttu-id="a8242-176">Komut `COPY` , Docker 'a bilgisayarınızdaki belirtilen klasörü kapsayıcıda bir klasöre kopyalamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="a8242-176">The `COPY` command tells Docker to copy the specified folder on your computer to a folder in the container.</span></span> <span data-ttu-id="a8242-177">Bu örnekte, **Publish** klasörü kapsayıcıda **uygulama** adlı bir klasöre kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="a8242-177">In this example, the **publish** folder is copied to a folder named **app** in the container.</span></span>

<span data-ttu-id="a8242-178">Sonraki komut `ENTRYPOINT`, Docker öğesine kapsayıcıyı yürütülebilir olarak çalışacak şekilde yapılandırmasını söyler.</span><span class="sxs-lookup"><span data-stu-id="a8242-178">The next command, `ENTRYPOINT`, tells Docker to configure the container to run as an executable.</span></span> <span data-ttu-id="a8242-179">Kapsayıcı başladığında, `ENTRYPOINT` komutu çalışır.</span><span class="sxs-lookup"><span data-stu-id="a8242-179">When the container starts, the `ENTRYPOINT` command runs.</span></span> <span data-ttu-id="a8242-180">Bu komut sona erdiğinde kapsayıcı otomatik olarak durur.</span><span class="sxs-lookup"><span data-stu-id="a8242-180">When this command ends, the container will automatically stop.</span></span>

<span data-ttu-id="a8242-181">Terminalinizden komutunu çalıştırın `docker build -t myimage -f Dockerfile .` ve komut tamamlandığında komutunu çalıştırın `docker images`.</span><span class="sxs-lookup"><span data-stu-id="a8242-181">From your terminal, run `docker build -t myimage -f Dockerfile .` and when that command finishes, run `docker images`.</span></span>

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

<span data-ttu-id="a8242-182">*Dockerfile* 'daki her komut bir katman oluşturdu ve BIR **görüntü kimliği**oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="a8242-182">Each command in the *Dockerfile* generated a layer and created an **IMAGE ID**.</span></span> <span data-ttu-id="a8242-183">Son **görüntü kimliği** (sizinki farklı olacak) **ddcc6646461b** ve bir sonraki adımda bu görüntüye göre bir kapsayıcı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a8242-183">The final **IMAGE ID** (yours will be different) is **ddcc6646461b** and next you'll create a container based on this image.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="a8242-184">Kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a8242-184">Create a container</span></span>

<span data-ttu-id="a8242-185">Artık uygulamanızı içeren bir görüntünüz olduğuna göre, bir kapsayıcı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8242-185">Now that you have an image that contains your app, you can create a container.</span></span> <span data-ttu-id="a8242-186">Bir kapsayıcıyı iki şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8242-186">You can create a container in two ways.</span></span> <span data-ttu-id="a8242-187">İlk olarak, durdurulan yeni bir kapsayıcı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a8242-187">First, create a new container that is stopped.</span></span>

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

<span data-ttu-id="a8242-188">Yukarıdaki komut, MyImage görüntüsünü temel alan bir kapsayıcı oluşturur. `docker create`</span><span class="sxs-lookup"><span data-stu-id="a8242-188">The `docker create` command from above will create a container based on the **myimage** image.</span></span> <span data-ttu-id="a8242-189">Bu komutun çıktısı, oluşturulan kapsayıcının **KAPSAYıCı kimliğini** (sizinki farklı olacak) gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8242-189">The output of that command shows you the **CONTAINER ID** (yours will be different) of the created container.</span></span> <span data-ttu-id="a8242-190">*Tüm* kapsayıcıların listesini görmek için `docker ps -a` komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a8242-190">To see a list of *all* containers, use the `docker ps -a` command:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a><span data-ttu-id="a8242-191">Kapsayıcıyı yönetme</span><span class="sxs-lookup"><span data-stu-id="a8242-191">Manage the container</span></span>

<span data-ttu-id="a8242-192">Her kapsayıcıya, bu kapsayıcı örneğine başvurmak için kullanabileceğiniz bir rastgele ad atanır.</span><span class="sxs-lookup"><span data-stu-id="a8242-192">Each container is assigned a random name that you can use to refer to that container instance.</span></span> <span data-ttu-id="a8242-193">Örneğin, otomatik olarak oluşturulan kapsayıcı **boring_matsumoto** adını (sizinki farklı olur) seçti ve bu ad kapsayıcıyı başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a8242-193">For example, the container that was created automatically chose the name **boring_matsumoto** (yours will be different) and that name can be used to start the container.</span></span> <span data-ttu-id="a8242-194">`docker create --name` Parametresini kullanarak otomatik adı belirli bir ile geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8242-194">You override the automatic name with a specific one by using the `docker create --name` parameter.</span></span>

<span data-ttu-id="a8242-195">Aşağıdaki örnek, kapsayıcıyı başlatmak `docker start` için komutunu kullanır ve sonra yalnızca çalıştıran kapsayıcıları göstermek için `docker ps` komutunu kullanır:</span><span class="sxs-lookup"><span data-stu-id="a8242-195">The following example uses the `docker start` command to start the container, and then uses the `docker ps` command to only show containers that are running:</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

<span data-ttu-id="a8242-196">Benzer şekilde, `docker stop` komut kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="a8242-196">Similarly, the `docker stop` command will stop the container.</span></span> <span data-ttu-id="a8242-197">Aşağıdaki örnek, kapsayıcıyı durdurmak `docker stop` için komutunu kullanır ve ardından hiçbir kapsayıcının çalışmadığını göstermek için `docker ps` komutunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8242-197">The following example uses the `docker stop` command to stop the container, and then uses the `docker ps` command to show that no containers are running.</span></span>

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a><span data-ttu-id="a8242-198">Bir kapsayıcıya bağlanma</span><span class="sxs-lookup"><span data-stu-id="a8242-198">Connect to a container</span></span>

<span data-ttu-id="a8242-199">Bir kapsayıcı çalışmaya başladıktan sonra çıktıyı görmek için bu sunucuya bağlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8242-199">After a container is running, you can connect to it to see the output.</span></span> <span data-ttu-id="a8242-200">`docker start` Ve`docker attach` komutlarını kullanarak kapsayıcıyı başlatın ve çıkış akışına göz atın.</span><span class="sxs-lookup"><span data-stu-id="a8242-200">Use the `docker start` and `docker attach` commands to start the container and peek at the output stream.</span></span> <span data-ttu-id="a8242-201">Bu örnekte, <kbd>CTRL + C</kbd> komutu, çalışan kapsayıcıyı ayırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a8242-201">In this example, the <kbd>CTRL + C</kbd> command is used to detach from the running container.</span></span> <span data-ttu-id="a8242-202">Bu işlem, kapsayıcıyı durduran kapsayıcıyı gerçekten sonlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="a8242-202">This may actually end the process in the container, which will stop the container.</span></span> <span data-ttu-id="a8242-203">Parametresi, <kbd>CTRL + C</kbd> 'nin kapsayıcıdaki işlemi durdurmamasını sağlar. `--sig-proxy=false`</span><span class="sxs-lookup"><span data-stu-id="a8242-203">The `--sig-proxy=false` parameter ensures that <kbd>CTRL + C</kbd> won't stop the process in the container.</span></span>

<span data-ttu-id="a8242-204">Kapsayıcıdan ayrıldıktan sonra, hala çalıştığını ve saymakta olduğunu doğrulamak için yeniden bağlayın.</span><span class="sxs-lookup"><span data-stu-id="a8242-204">After you detach from the container, reattach to verify that it's still running and counting.</span></span>

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a><span data-ttu-id="a8242-205">Kapsayıcıyı silme</span><span class="sxs-lookup"><span data-stu-id="a8242-205">Delete a container</span></span>

<span data-ttu-id="a8242-206">Bu makalenin amaçları doğrultusunda, kapsayıcıların hiçbir şey yapmadan asılı istememeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a8242-206">For the purposes of this article you don't want containers just hanging around doing nothing.</span></span> <span data-ttu-id="a8242-207">Daha önce oluşturduğunuz kapsayıcıyı silin.</span><span class="sxs-lookup"><span data-stu-id="a8242-207">Delete the container you previously created.</span></span> <span data-ttu-id="a8242-208">Kapsayıcı çalışıyorsa durdurun.</span><span class="sxs-lookup"><span data-stu-id="a8242-208">If the container is running, stop it.</span></span>

```console
> docker stop boring_matsumoto
```

<span data-ttu-id="a8242-209">Aşağıdaki örnekte tüm kapsayıcılar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a8242-209">The following example lists all containers.</span></span> <span data-ttu-id="a8242-210">Ardından, kapsayıcıyı silmek `docker rm` için komutunu kullanır ve ardından çalışan kapsayıcılar için ikinci bir kez kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="a8242-210">It then uses the `docker rm` command to delete the container, and then checks a second time for any running containers.</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a><span data-ttu-id="a8242-211">Tek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a8242-211">Single run</span></span>

<span data-ttu-id="a8242-212">Docker, kapsayıcıyı `docker run` tek bir komut olarak oluşturup çalıştırmak için komutunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8242-212">Docker provides the `docker run` command to create and run the container as a single command.</span></span> <span data-ttu-id="a8242-213">Bu komut, ve daha sonra `docker create` `docker start`çalıştırma gereksinimini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a8242-213">This command eliminates the need to run `docker create` and then `docker start`.</span></span> <span data-ttu-id="a8242-214">Kapsayıcı durdurulduğunda kapsayıcıyı otomatik olarak silmek için de bu komutu ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8242-214">You can also set this command to automatically delete the container when the container stops.</span></span> <span data-ttu-id="a8242-215">Örneğin, ilk olarak `docker run -it --rm` iki şey yapmak için kullanın, kapsayıcıya bağlanmak için otomatik olarak geçerli terminali kullanın ve ardından kapsayıcı tamamlandığında onu kaldırın:</span><span class="sxs-lookup"><span data-stu-id="a8242-215">For example, use `docker run -it --rm` to do two things, first, automatically use the current terminal to connect to the container, and then when the container finishes, remove it:</span></span>

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

<span data-ttu-id="a8242-216">İle `docker run -it`, <kbd>CTRL + C</kbd> komutu kapsayıcıda çalışan işlemi durdurur, bu da kapsayıcıyı durdurur.</span><span class="sxs-lookup"><span data-stu-id="a8242-216">With `docker run -it`, the <kbd>CTRL + C</kbd> command will stop process that is running in the container, which in turn, stops the container.</span></span> <span data-ttu-id="a8242-217">`--rm` Parametre sağlandığı için, işlem durdurulduğunda kapsayıcı otomatik olarak silinir.</span><span class="sxs-lookup"><span data-stu-id="a8242-217">Since the `--rm` parameter was provided, the container is automatically deleted when the process is stopped.</span></span> <span data-ttu-id="a8242-218">Mevcut olmadığını doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="a8242-218">Verify that it does not exist:</span></span>

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a><span data-ttu-id="a8242-219">GIRIŞ noktasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="a8242-219">Change the ENTRYPOINT</span></span>

<span data-ttu-id="a8242-220">Komut ayrıca *dockerfile* ' dan `ENTRYPOINT` komutu değiştirmenize ve yalnızca bu kapsayıcı için, başka bir şey çalıştırmanıza imkan tanır. `docker run`</span><span class="sxs-lookup"><span data-stu-id="a8242-220">The `docker run` command also lets you modify the `ENTRYPOINT` command from the *Dockerfile* and run something else, but only for that container.</span></span> <span data-ttu-id="a8242-221">Örneğin, veya `bash` `cmd.exe`çalıştırmak için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8242-221">For example, use the following command to run `bash` or `cmd.exe`.</span></span> <span data-ttu-id="a8242-222">Komutu gereken şekilde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="a8242-222">Edit the command as necessary.</span></span>

#### <a name="windows"></a><span data-ttu-id="a8242-223">Windows</span><span class="sxs-lookup"><span data-stu-id="a8242-223">Windows</span></span>
<span data-ttu-id="a8242-224">Bu örnekte, `ENTRYPOINT` olarak `cmd.exe`değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="a8242-224">In this example, `ENTRYPOINT` is changed to `cmd.exe`.</span></span> <span data-ttu-id="a8242-225">İşlemi sonlandırmak ve kapsayıcıyı durdurmak için <kbd>CTRL + C</kbd> tuşlarına basıldığında.</span><span class="sxs-lookup"><span data-stu-id="a8242-225"><kbd>CTRL + C</kbd> is pressed to end the process and stop the container.</span></span>

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

#### <a name="linux"></a><span data-ttu-id="a8242-226">Linux</span><span class="sxs-lookup"><span data-stu-id="a8242-226">Linux</span></span>

<span data-ttu-id="a8242-227">Bu örnekte, `ENTRYPOINT` olarak `bash`değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="a8242-227">In this example, `ENTRYPOINT` is changed to `bash`.</span></span> <span data-ttu-id="a8242-228">`quit` Komut, işlemi sonlandıran ve kapsayıcıyı durduran çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="a8242-228">The `quit` command is run which ends the process and stop the container.</span></span>

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a><span data-ttu-id="a8242-229">Gerekli komutlar</span><span class="sxs-lookup"><span data-stu-id="a8242-229">Essential commands</span></span>

<span data-ttu-id="a8242-230">Docker, kapsayıcınıza ve görüntülerinize ne yapmak istediğinizi kapsayan birçok farklı komuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a8242-230">Docker has many different commands that cover what you want to do with your container and images.</span></span> <span data-ttu-id="a8242-231">Bu Docker komutları, Kapsayıcılarınızı yönetmek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="a8242-231">These Docker commands are essential to managing your containers:</span></span>

* [<span data-ttu-id="a8242-232">Docker derlemesi</span><span class="sxs-lookup"><span data-stu-id="a8242-232">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="a8242-233">Docker çalıştırma</span><span class="sxs-lookup"><span data-stu-id="a8242-233">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="a8242-234">Docker PS</span><span class="sxs-lookup"><span data-stu-id="a8242-234">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="a8242-235">Docker durdur</span><span class="sxs-lookup"><span data-stu-id="a8242-235">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="a8242-236">Docker RM</span><span class="sxs-lookup"><span data-stu-id="a8242-236">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="a8242-237">Docker rmi</span><span class="sxs-lookup"><span data-stu-id="a8242-237">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="a8242-238">Docker görüntüsü</span><span class="sxs-lookup"><span data-stu-id="a8242-238">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a><span data-ttu-id="a8242-239">Kaynakları temizleme</span><span class="sxs-lookup"><span data-stu-id="a8242-239">Clean up resources</span></span>

<span data-ttu-id="a8242-240">Bu öğreticide kapsayıcılar ve görüntüler oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="a8242-240">During this tutorial you created containers and images.</span></span> <span data-ttu-id="a8242-241">İsterseniz, bu kaynakları silin.</span><span class="sxs-lookup"><span data-stu-id="a8242-241">If you want, delete these resources.</span></span> <span data-ttu-id="a8242-242">İçin aşağıdaki komutları kullanın</span><span class="sxs-lookup"><span data-stu-id="a8242-242">Use the following commands to</span></span>

01. <span data-ttu-id="a8242-243">Tüm kapsayıcıları Listele</span><span class="sxs-lookup"><span data-stu-id="a8242-243">List all containers</span></span>

    ```console
    > docker ps -a
    ```

02. <span data-ttu-id="a8242-244">Çalıştıran kapsayıcıları durdurun.</span><span class="sxs-lookup"><span data-stu-id="a8242-244">Stop containers that are running.</span></span> <span data-ttu-id="a8242-245">, `CONTAINER_NAME` Kapsayıcıya otomatik olarak atanan adı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8242-245">The `CONTAINER_NAME` represents the name automatically assigned to the container.</span></span>

    ```console
    > docker stop CONTAINER_NAME
    ```

03. <span data-ttu-id="a8242-246">Kapsayıcıyı sil</span><span class="sxs-lookup"><span data-stu-id="a8242-246">Delete the container</span></span>

    ```console
    > docker rm CONTAINER_NAME
    ```

<span data-ttu-id="a8242-247">Sonra, makinenizde artık istemediğiniz görüntüleri silin.</span><span class="sxs-lookup"><span data-stu-id="a8242-247">Next, delete any images that you no longer want on your machine.</span></span> <span data-ttu-id="a8242-248">*Dockerfile* dosyanız tarafından oluşturulan görüntüyü silin ve ardından *dockerfile* ' ın dayandığı .NET Core görüntüsünü silin.</span><span class="sxs-lookup"><span data-stu-id="a8242-248">Delete the image created by your *Dockerfile* and then delete the .NET Core image the *Dockerfile* was based on.</span></span> <span data-ttu-id="a8242-249">**Görüntü kimliğini** veya **Depo: etiketli dize etiketini** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8242-249">You can use the **IMAGE ID** or the **REPOSITORY:TAG** formatted string.</span></span>

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

<span data-ttu-id="a8242-250">Yüklenen görüntülerin listesini görmek için komutunukullanın.`docker images`</span><span class="sxs-lookup"><span data-stu-id="a8242-250">Use the `docker images` command to see a list of images installed.</span></span>

> [!NOTE]
> <span data-ttu-id="a8242-251">Görüntü dosyaları büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8242-251">Image files can be large.</span></span> <span data-ttu-id="a8242-252">Genellikle, uygulamanızı test ederken ve geliştirirken oluşturduğunuz geçici kapsayıcıları kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="a8242-252">Typically, you would remove temporary containers you created while testing and developing your app.</span></span> <span data-ttu-id="a8242-253">Bu çalışma zamanına göre diğer görüntüleri oluşturmayı planlıyorsanız, genellikle temel görüntüleri çalışma zamanı yüklü olarak tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a8242-253">You usually keep the base images with the runtime installed if you plan on building other images based on that runtime.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a8242-254">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a8242-254">Next steps</span></span>

* [<span data-ttu-id="a8242-255">ASP.NET Core mikro hizmet öğreticisini deneyin.</span><span class="sxs-lookup"><span data-stu-id="a8242-255">Try the ASP.NET Core Microservice Tutorial.</span></span>](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [<span data-ttu-id="a8242-256">Kapsayıcıları destekleyen Azure hizmetlerini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="a8242-256">Review the Azure services that support containers.</span></span>](https://azure.microsoft.com/overview/containers/)
* [<span data-ttu-id="a8242-257">Dockerfile komutları hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="a8242-257">Read about Dockerfile commands.</span></span>](https://docs.docker.com/engine/reference/builder/)
* [<span data-ttu-id="a8242-258">Visual Studio için kapsayıcı araçlarını keşfet</span><span class="sxs-lookup"><span data-stu-id="a8242-258">Explore the Container Tools for Visual Studio</span></span>](/visualstudio/containers/overview)

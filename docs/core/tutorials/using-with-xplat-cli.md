---
title: CLI kullanarak .NET Core'u kullanmaya başlama
description: Windows, Linux veya .NET Core komut satırı arabirimi (CLI) kullanarak macOS .NET Core kullanmaya başlamak nasıl gösteren adım adım öğretici.
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 23aec1b951c4b65d62bd4da4b4c94043b1411cf3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="9759b-103">Windows/Linux/macOS komut satırını kullanarak .NET Çekirdeğinde ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="9759b-103">Getting started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="9759b-104">Bu konu .NET Core CLI araçlarını kullanarak makinenizdeki platformlar arası uygulamaları geliştirmeye başlamak nasıl yapacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9759b-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="9759b-105">.NET Core CLI araç takımı değilseniz, okuma [.NET Core SDK Genel Bakış](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="9759b-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9759b-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9759b-106">Prerequisites</span></span>

- <span data-ttu-id="9759b-107">[.NET core SDK 1.0](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="9759b-107">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="9759b-108">Bir metin düzenleyicisi veya kod düzenleyiciyi.</span><span class="sxs-lookup"><span data-stu-id="9759b-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="9759b-109">Merhaba, konsol uygulaması!</span><span class="sxs-lookup"><span data-stu-id="9759b-109">Hello, Console App!</span></span>

<span data-ttu-id="9759b-110">Yapabilecekleriniz [görüntülemek veya karşıdan örnek kod](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) dotnet/samples Github'da depodan.</span><span class="sxs-lookup"><span data-stu-id="9759b-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="9759b-111">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9759b-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="9759b-112">Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*.</span><span class="sxs-lookup"><span data-stu-id="9759b-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="9759b-113">Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="9759b-113">Navigate to the folder you created and type the following:</span></span>

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

<span data-ttu-id="9759b-114">Şimdi hızlı bir kılavuz yapın:</span><span class="sxs-lookup"><span data-stu-id="9759b-114">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="9759b-115">[`dotnet new`](../tools/dotnet-new.md) güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak için gereken bağımlılıkları olan proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="9759b-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="9759b-116">Ayrıca oluşturur bir `Program.cs`, uygulama için giriş noktası içeren temel bir dosya.</span><span class="sxs-lookup"><span data-stu-id="9759b-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="9759b-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="9759b-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   <span data-ttu-id="9759b-118">Proje dosyası bağımlılıkları geri yükleyin ve programı oluşturmak için gerekli olan her şeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="9759b-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="9759b-119">`OutputType` Etiketi bir yürütülebilir dosya, diğer bir deyişle bir konsol uygulaması oluşturduğunuz belirtir.</span><span class="sxs-lookup"><span data-stu-id="9759b-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="9759b-120">`TargetFramework` Etiketi hedefleme hangi .NET uygulaması belirtir.</span><span class="sxs-lookup"><span data-stu-id="9759b-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="9759b-121">Gelişmiş bir senaryo da birden çok hedef çerçeveyi belirtin ve tüm yapı tek bir işlem de.</span><span class="sxs-lookup"><span data-stu-id="9759b-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="9759b-122">Bu öğreticide, biz yalnızca .NET çekirdeği 1.0 için yapı takılıyor.</span><span class="sxs-lookup"><span data-stu-id="9759b-122">In this tutorial, we'll stick to building only for .NET Core 1.0.</span></span>

   <span data-ttu-id="9759b-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="9759b-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   <span data-ttu-id="9759b-124">Tarafından programı başlatan `using System`, anlamına gelen "her şeyi Getir `System` bu dosya için kapsam içine ad".</span><span class="sxs-lookup"><span data-stu-id="9759b-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="9759b-125">`System` Ad alanı içeren temel yapıları gibi `string`, veya sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="9759b-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="9759b-126">Ardından adlı bir ad alanı tanımlarız `Hello`.</span><span class="sxs-lookup"><span data-stu-id="9759b-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="9759b-127">Bu, istediğiniz bir şey değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9759b-127">You can change this to anything you want.</span></span> <span data-ttu-id="9759b-128">Adlı bir sınıf `Program` ad alanında, ile tanımlanmış bir `Main` yönteminin dizisini kendi bağımsız değişken olarak alan.</span><span class="sxs-lookup"><span data-stu-id="9759b-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="9759b-129">Bu dizi derlenmiş program çağrıldığında geçirilen bağımsız değişkenlerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9759b-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="9759b-130">Olduğu gibi bu diziye kullanılmaz: program yapılması şey "Hello World!" yazmak için</span><span class="sxs-lookup"><span data-stu-id="9759b-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="9759b-131">konsola.</span><span class="sxs-lookup"><span data-stu-id="9759b-131">to the console.</span></span> <span data-ttu-id="9759b-132">Daha sonra değişiklikler yapacak kodu vermiyoruz bu değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="9759b-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   <span data-ttu-id="9759b-133">[`dotnet restore`](../tools/dotnet-restore.md) içine çağırır [NuGet](https://www.nuget.org/) (bağımlılıkları ağacının geri yüklemek için Paket Yöneticisi .NET).</span><span class="sxs-lookup"><span data-stu-id="9759b-133">[`dotnet restore`](../tools/dotnet-restore.md) calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="9759b-134">NuGet çözümler *Hello.csproj* dosya, dosyasında belirtilen bağımlılıkları indirir (veya bunları makinenizde önbellekten alan) ve Yazar *obj/project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="9759b-134">NuGet analyzes the *Hello.csproj* file, downloads the dependencies stated in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file.</span></span>  <span data-ttu-id="9759b-135">*Project.assets.json* derlemek ve çalıştırmak dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9759b-135">The *project.assets.json* file is necessary to be able to compile and run.</span></span>
   
   <span data-ttu-id="9759b-136">*Project.assets.json* NuGet bağımlılıklar ve bir uygulamayı açıklayan diğer bilgi grafiği kalıcı ve eksiksiz bir kümesini bir dosyadır.</span><span class="sxs-lookup"><span data-stu-id="9759b-136">The *project.assets.json* file is a persisted and complete set of the graph of NuGet dependencies and other information describing an app.</span></span>  <span data-ttu-id="9759b-137">Bu dosyayı gibi diğer araçları tarafından okuma [ `dotnet build` ](../tools/dotnet-build.md) ve [ `dotnet run` ](../tools/dotnet-run.md), bunları işleme NuGet bağımlılıkları doğru kümesiyle kaynak kodu etkinleştirme ve bağlama çözümler.</span><span class="sxs-lookup"><span data-stu-id="9759b-137">This file is read by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), enabling them to process the source code with a correct set of NuGet dependencies and binding resolutions.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="9759b-138">[`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) hedefleri yerleşik yapı ve çağrıları emin olmak için `dotnet <assembly.dll>` hedef uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9759b-138">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>
   
    ```
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="9759b-139">Alternatif olarak, aynı zamanda yürütebilirsiniz [ `dotnet build` ](../tools/dotnet-build.md) konsol uygulamaları derleme çalıştırmadan Kodu derlemek için.</span><span class="sxs-lookup"><span data-stu-id="9759b-139">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="9759b-140">Bu ile çalıştırılabilir bir DLL dosyası olarak derlenmiş bir uygulamada sonuçları `dotnet bin\Debug\netcoreapp1.0\Hello.dll` Windows (kullanmak `/` Windows olmayan sistemler için).</span><span class="sxs-lookup"><span data-stu-id="9759b-140">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp1.0\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="9759b-141">Daha sonra konusunda anlatıldığı gibi uygulamaya bağımsız değişkenler de belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="9759b-141">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="9759b-142">Gelişmiş bir senaryo dağıtılan ve mutlaka .NET Core yüklü olmayan bir makineye çalıştırmak platforma özel dosyaları müstakil kümesi olarak uygulama oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="9759b-142">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="9759b-143">Bkz: [.NET Core uygulama dağıtımı](../deploying/index.md) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="9759b-143">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="9759b-144">Program program.cs'ye</span><span class="sxs-lookup"><span data-stu-id="9759b-144">Augmenting the program</span></span>

<span data-ttu-id="9759b-145">Bir bit program değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="9759b-145">Let's change the program a bit.</span></span> <span data-ttu-id="9759b-146">Fun Fibonacci numaralarıdır, kişinin selam için bağımsız değişken kullanım yanı sıra uygulama çalışırken sağlandığından ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9759b-146">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="9759b-147">Değiştir, *Program.cs* aşağıdaki kod ile dosya:</span><span class="sxs-lookup"><span data-stu-id="9759b-147">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. <span data-ttu-id="9759b-148">Yürütme [ `dotnet build` ](../tools/dotnet-build.md) değişiklikleri derlemek için.</span><span class="sxs-lookup"><span data-stu-id="9759b-148">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="9759b-149">Uygulama için bir parametre geçirme programı çalıştır:</span><span class="sxs-lookup"><span data-stu-id="9759b-149">Run the program passing a parameter to the app:</span></span>

   ```
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

<span data-ttu-id="9759b-150">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="9759b-150">And that's it!</span></span>  <span data-ttu-id="9759b-151">Büyütmek `Program.cs` istediğiniz gibi.</span><span class="sxs-lookup"><span data-stu-id="9759b-151">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="9759b-152">Birden çok dosyalarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="9759b-152">Working with multiple files</span></span>

<span data-ttu-id="9759b-153">Tek dosyalar için basit bir kerelik programlar ince, ancak daha karmaşık bir uygulama oluşturuyorsanız, büyük olasılıkla birden fazla kaynak dosya projenizi şimdi yükleneceği yapı önceki Fibonacci örnek dışına bazı Fibonacci değerler önbelleğe alarak olduğunuz ve bazı özyinelemeli ekleyin Özellikler.</span><span class="sxs-lookup"><span data-stu-id="9759b-153">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span> 

1. <span data-ttu-id="9759b-154">İçinde yeni bir dosya ekleyin *Hello* adlı dizin *FibonacciGenerator.cs* aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="9759b-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. <span data-ttu-id="9759b-155">Değişiklik `Main` yönteminde, *Program.cs* dosyasını yeni sınıfının örneği ve aşağıdaki örnekteki gibi yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="9759b-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="9759b-156">Yürütme [ `dotnet build` ](../tools/dotnet-build.md) değişiklikleri derlemek için.</span><span class="sxs-lookup"><span data-stu-id="9759b-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="9759b-157">Yürüterek uygulamanızı çalıştırma [ `dotnet run` ](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="9759b-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="9759b-158">Aşağıdaki program çıkış şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="9759b-158">The following shows the program output:</span></span>

   ```
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

<span data-ttu-id="9759b-159">Ve bu kadar!</span><span class="sxs-lookup"><span data-stu-id="9759b-159">And that's it!</span></span> <span data-ttu-id="9759b-160">Şimdi, temel kavramları kendi programlar oluşturmak için buraya öğrenilen kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9759b-160">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="9759b-161">Komutlar ve uygulamanızı çalıştırmak için Bu öğreticide gösterilen adımlar yalnızca geliştirme zamanı sırasında kullanılan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9759b-161">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="9759b-162">Uygulamanızı dağıtmak hazır olduğunuzda, farklı bir göz atalım istersiniz [dağıtım stratejilerini](../deploying/index.md) .NET Core uygulamaları için ve [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="9759b-162">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="9759b-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9759b-163">See also</span></span>

[<span data-ttu-id="9759b-164">Düzenleme ve projeleri .NET Core CLI araçları ile test etme</span><span class="sxs-lookup"><span data-stu-id="9759b-164">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)

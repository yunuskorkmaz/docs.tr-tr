---
title: CLI kullanarak .NET Core ile çalışmaya başlama
description: Windows, Linux veya .NET Core komut satırı arabirimi (CLI) kullanarak macOS üzerinde .NET Core ile çalışmaya başlama gösteren adım adım bir öğretici.
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.technology: dotnet-cli
ms.openlocfilehash: 5ec7168ebc2ee4fc428d1ab520e986842f111ca7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564646"
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="cecd5-103">Windows/Linus/macos'ta komut satırını kullanarak .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="cecd5-103">Getting started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="cecd5-104">Bu konuda, makinenizde .NET Core CLI araçları ile platformlar arası uygulamalar geliştirmeye başlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="cecd5-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="cecd5-105">.NET Core CLI araç takımıyla bilmiyorsanız, okuma [.NET Core SDK'sı genel bakış](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="cecd5-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cecd5-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cecd5-106">Prerequisites</span></span>

- <span data-ttu-id="cecd5-107">[.NET core SDK'sı 1.0](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="cecd5-107">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="cecd5-108">Bir metin düzenleyicisi veya tercih ettiğiniz Kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="cecd5-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="cecd5-109">Konsol uygulaması Merhaba!</span><span class="sxs-lookup"><span data-stu-id="cecd5-109">Hello, Console App!</span></span>

<span data-ttu-id="cecd5-110">Yapabilecekleriniz [görüntülemek veya örnek kodu indirdikten](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) dotnet/samples GitHub deposundan.</span><span class="sxs-lookup"><span data-stu-id="cecd5-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="cecd5-111">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="cecd5-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="cecd5-112">Bir komut istemi açın ve adlı bir klasör oluşturun *Hello*.</span><span class="sxs-lookup"><span data-stu-id="cecd5-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="cecd5-113">Oluşturduğunuz klasöre gidin ve aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="cecd5-113">Navigate to the folder you created and type the following:</span></span>

```console
$ dotnet new console
$ dotnet restore
$ dotnet run
```

<span data-ttu-id="cecd5-114">Hızlı bir kılavuz inceleyelim:</span><span class="sxs-lookup"><span data-stu-id="cecd5-114">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="cecd5-115">[`dotnet new`](../tools/dotnet-new.md) güncel bir oluşturur `Hello.csproj` bir konsol uygulaması oluşturmak gerekli bağımlılıkları olan proje dosyası.</span><span class="sxs-lookup"><span data-stu-id="cecd5-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="cecd5-116">Ayrıca oluşturur bir `Program.cs`, uygulamanın giriş noktasını içeren temel bir dosya.</span><span class="sxs-lookup"><span data-stu-id="cecd5-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="cecd5-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="cecd5-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="cecd5-118">Proje dosyası geri yükleme bağımlılıkları ve program oluşturmak için gerekli olan her şeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="cecd5-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="cecd5-119">`OutputType` Etiketini belirtir bir yürütülebilir dosya, başka bir deyişle bir konsol uygulaması oluşturuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="cecd5-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="cecd5-120">`TargetFramework` Hedefleyen hangi .NET uygulaması etiketini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cecd5-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="cecd5-121">Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtin ve tüm yapı tek bir işlemde olanlar.</span><span class="sxs-lookup"><span data-stu-id="cecd5-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="cecd5-122">Bu öğreticide, biz yalnızca .NET Core 1.0 için yapı için kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="cecd5-122">In this tutorial, we'll stick to building only for .NET Core 1.0.</span></span>

   <span data-ttu-id="cecd5-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="cecd5-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="cecd5-124">Tarafından program başlar `using System`, anlamına "her şey Getir `System` kapsama bu dosya için ad alanı".</span><span class="sxs-lookup"><span data-stu-id="cecd5-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="cecd5-125">`System` Ad alanı içeren temel yapılarından gibi `string`, ya da sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="cecd5-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="cecd5-126">Ad alanı ardından tanımlarız `Hello`.</span><span class="sxs-lookup"><span data-stu-id="cecd5-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="cecd5-127">Bu için istediğiniz değişikliği yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cecd5-127">You can change this to anything you want.</span></span> <span data-ttu-id="cecd5-128">Adlı bir sınıf `Program` ile bu ad alanı içinde tanımlanan bir `Main` dizisini kendi bağımsız değişkeni olarak alan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cecd5-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="cecd5-129">Bu dizi, derlenmiş programın çağrılırken geçirilen bağımsız değişken listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="cecd5-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="cecd5-130">Olduğu gibi bu dizinin kullanılmaz: "Hello World!" yazmak için tüm programı yaptığını olduğu</span><span class="sxs-lookup"><span data-stu-id="cecd5-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="cecd5-131">konsola.</span><span class="sxs-lookup"><span data-stu-id="cecd5-131">to the console.</span></span> <span data-ttu-id="cecd5-132">Değişiklikleri olmanızı sağlayacak kodu daha sonra oluşturacağız bu değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="cecd5-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   <span data-ttu-id="cecd5-133">[`dotnet restore`](../tools/dotnet-restore.md) içine yapılan çağrılar [NuGet](https://www.nuget.org/) (bağımlılıkları ağacının geri yüklemek için Paket Yöneticisi .NET).</span><span class="sxs-lookup"><span data-stu-id="cecd5-133">[`dotnet restore`](../tools/dotnet-restore.md) calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="cecd5-134">NuGet çözümler *Hello.csproj* dosya, dosyasında belirtilen bağımlılıkları indirir (veya bunları makinenizde önbellekten Dallarınızla) ve Yazar *obj/project.assets.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="cecd5-134">NuGet analyzes the *Hello.csproj* file, downloads the dependencies stated in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file.</span></span>  <span data-ttu-id="cecd5-135">*Project.assets.json* derlemek ve çalıştırmak dosya gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cecd5-135">The *project.assets.json* file is necessary to be able to compile and run.</span></span>

   <span data-ttu-id="cecd5-136">*Project.assets.json* grafiği, NuGet bağımlılıklarını ve uygulamayı açıklayan diğer bilgilerin kalıcı ve eksiksiz bir kümesini dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="cecd5-136">The *project.assets.json* file is a persisted and complete set of the graph of NuGet dependencies and other information describing an app.</span></span>  <span data-ttu-id="cecd5-137">Bu dosya gibi diğer araçları tarafından okunur [ `dotnet build` ](../tools/dotnet-build.md) ve [ `dotnet run` ](../tools/dotnet-run.md), NuGet bağımlılıklarını doğru bir dizi kaynak koduyla işlenecek dönemlik ve çözümleri bağlama.</span><span class="sxs-lookup"><span data-stu-id="cecd5-137">This file is read by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), enabling them to process the source code with a correct set of NuGet dependencies and binding resolutions.</span></span>

3. `$ dotnet run`

   <span data-ttu-id="cecd5-138">[`dotnet run`](../tools/dotnet-run.md) çağrıları [ `dotnet build` ](../tools/dotnet-build.md) hedefleri oluşturulan derleme ve çağrıları emin olmak için `dotnet <assembly.dll>` hedef uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cecd5-138">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="cecd5-139">Alternatif olarak, aynı zamanda yürütebilirsiniz [ `dotnet build` ](../tools/dotnet-build.md) konsol uygulamaları derleme çalıştırmadan Kodu derlemek için.</span><span class="sxs-lookup"><span data-stu-id="cecd5-139">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="cecd5-140">İle çalıştırılabilir bir DLL dosyası olarak derlenmiş bir uygulama sonuçlanır `dotnet bin\Debug\netcoreapp1.0\Hello.dll` Windows üzerinde (kullanın `/` Windows olmayan sistemler için).</span><span class="sxs-lookup"><span data-stu-id="cecd5-140">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp1.0\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="cecd5-141">Bu konuda daha sonra göreceğiniz üzere uygulamaya bağımsız değişkenler de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cecd5-141">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="cecd5-142">Gelişmiş bir senaryo dağıtılabilir ve .NET Core yüklü olmak zorunda olmayan bir makineye çalıştırma platforma özgü dosyaları kendi içinde bir dizi olarak uygulama oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="cecd5-142">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="cecd5-143">Bkz: [.NET Core uygulaması dağıtımını](../deploying/index.md) Ayrıntılar için.</span><span class="sxs-lookup"><span data-stu-id="cecd5-143">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="cecd5-144">Program deneyimlerinizi</span><span class="sxs-lookup"><span data-stu-id="cecd5-144">Augmenting the program</span></span>

<span data-ttu-id="cecd5-145">Bir bit program değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="cecd5-145">Let's change the program a bit.</span></span> <span data-ttu-id="cecd5-146">Eğlenceli Fibonacci sayılardır, kişi selam bağımsız değişkenin kullanım hakkına ek olarak uygulama çalıştıran şimdi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cecd5-146">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="cecd5-147">Öğesinin içeriğini değiştirin, *Program.cs* dosyasındaki kodu aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="cecd5-147">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="cecd5-148">Yürütme [ `dotnet build` ](../tools/dotnet-build.md) değişiklikleri derlemek için.</span><span class="sxs-lookup"><span data-stu-id="cecd5-148">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="cecd5-149">Uygulamaya bir parametre geçirerek programı çalıştır:</span><span class="sxs-lookup"><span data-stu-id="cecd5-149">Run the program passing a parameter to the app:</span></span>

   ```console
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

<span data-ttu-id="cecd5-150">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="cecd5-150">And that's it!</span></span>  <span data-ttu-id="cecd5-151">Genişletmek `Program.cs` istediğiniz gibi.</span><span class="sxs-lookup"><span data-stu-id="cecd5-151">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="cecd5-152">Birden çok dosyaları ile çalışma</span><span class="sxs-lookup"><span data-stu-id="cecd5-152">Working with multiple files</span></span>

<span data-ttu-id="cecd5-153">Tek dosyalar için basit bir kerelik programlar bir sakınca yoktur ancak daha karmaşık bir uygulama oluşturuyorsanız, büyük olasılıkla birden çok kaynak dosyaları projenize şimdi yükleneceği derleme önceki Fibonacci örnek alanlarını bazı Fibonacci değerleri önbelleğe alarak olduğunuz ve bazı özyinelemeli Ekle Özellikler.</span><span class="sxs-lookup"><span data-stu-id="cecd5-153">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="cecd5-154">İçinde yeni bir dosya ekleme *Hello* adlı dizin *FibonacciGenerator.cs* aşağıdaki kod ile:</span><span class="sxs-lookup"><span data-stu-id="cecd5-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="cecd5-155">Değişiklik `Main` yönteminde, *Program.cs* dosya yeni bir sınıf örneği oluşturun ve aşağıdaki örnekte olduğu gibi yöntem çağırmak için:</span><span class="sxs-lookup"><span data-stu-id="cecd5-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="cecd5-156">Yürütme [ `dotnet build` ](../tools/dotnet-build.md) değişiklikleri derlemek için.</span><span class="sxs-lookup"><span data-stu-id="cecd5-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="cecd5-157">Yürüterek uygulamanızı çalıştırma [ `dotnet run` ](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="cecd5-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="cecd5-158">Program çıktısı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cecd5-158">The following shows the program output:</span></span>

   ```console
   $ dotnet run
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

<span data-ttu-id="cecd5-159">Ve İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="cecd5-159">And that's it!</span></span> <span data-ttu-id="cecd5-160">Şimdi burada kendi programlar oluşturmak için temel kavramları öğrendiniz kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cecd5-160">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="cecd5-161">Komutlar ve uygulamanızı çalıştırmak için Bu öğreticide gösterilen adımlar yalnızca geliştirme zamanı sırasında kullanıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cecd5-161">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="cecd5-162">Uygulamanızı dağıtmak hazır olduğunuzda, farklı bir göz atın isteyeceksiniz [dağıtım stratejilerini](../deploying/index.md) .NET Core uygulamaları için ve [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="cecd5-162">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="cecd5-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cecd5-163">See also</span></span>

* [<span data-ttu-id="cecd5-164">Düzenleme ve .NET Core CLI araçları ile projeleri test etme</span><span class="sxs-lookup"><span data-stu-id="cecd5-164">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)

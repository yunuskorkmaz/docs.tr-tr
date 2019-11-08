---
title: CLı kullanarak .NET Core ile çalışmaya başlama
description: .NET Core komut satırı arabirimi (CLı) kullanarak Windows, Linux veya macOS 'ta .NET Core ile çalışmaya başlama hakkında adım adım öğretici.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: cf8c3ae070f4c77789dc55ba4d7888c7b15c8653
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736983"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="387f7-103">Komut satırını kullanarak Windows/Linux/macOS 'ta .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="387f7-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="387f7-104">Bu konu, .NET Core CLI araçları kullanılarak makinenizde platformlar arası uygulamalar geliştirmeye nasıl başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="387f7-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="387f7-105">.NET Core CLI araç takımını tanımıyorsanız, [.NET Core SDK genel bakış](../tools/index.md)makalesini okuyun.</span><span class="sxs-lookup"><span data-stu-id="387f7-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="387f7-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="387f7-106">Prerequisites</span></span>

- <span data-ttu-id="387f7-107">[.NET Core SDK 2,1](https://dotnet.microsoft.com/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="387f7-107">[.NET Core SDK 2.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="387f7-108">Seçtiğiniz bir metin düzenleyici veya kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="387f7-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="387f7-109">Merhaba, konsol uygulaması!</span><span class="sxs-lookup"><span data-stu-id="387f7-109">Hello, Console App!</span></span>

<span data-ttu-id="387f7-110">Örnek kodu DotNet/Samples GitHub deposundan [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) .</span><span class="sxs-lookup"><span data-stu-id="387f7-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="387f7-111">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="387f7-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="387f7-112">Bir komut istemi açın ve *Hello*adlı bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="387f7-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="387f7-113">Oluşturduğunuz klasöre gidin ve aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="387f7-113">Navigate to the folder you created and type the following:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="387f7-114">Hızlı bir yol açalım:</span><span class="sxs-lookup"><span data-stu-id="387f7-114">Let's do a quick walkthrough:</span></span>

1. `dotnet new console`

   <span data-ttu-id="387f7-115">[`dotnet new`](../tools/dotnet-new.md) , bir konsol uygulaması oluşturmak için gereken bağımlılıklara sahip bir güncel *Hello. csproj* proje dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="387f7-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="387f7-116">Ayrıca, uygulamanın giriş noktasını içeren temel bir dosya olan bir *program.cs*oluşturur.</span><span class="sxs-lookup"><span data-stu-id="387f7-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="387f7-117">*Merhaba. csproj*:</span><span class="sxs-lookup"><span data-stu-id="387f7-117">*Hello.csproj*:</span></span>

   [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="387f7-118">Proje dosyası, bağımlılıkları geri yüklemek ve programı derlemek için gereken her şeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="387f7-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   - <span data-ttu-id="387f7-119">`OutputType` etiketi, bir konsol uygulaması diğer bir deyişle yürütülebilir bir dosya oluşturduğumuz olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="387f7-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   - <span data-ttu-id="387f7-120">`TargetFramework` etiketi, hangi .NET uygulamasının hedefleyebileceklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="387f7-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="387f7-121">Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtebilir ve tek bir işlemde bunların tümüne derleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f7-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="387f7-122">Bu öğreticide yalnızca .NET Core 2,1 için derleme yapacağız.</span><span class="sxs-lookup"><span data-stu-id="387f7-122">In this tutorial, we'll stick to building only for .NET Core 2.1.</span></span>

   <span data-ttu-id="387f7-123">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="387f7-123">*Program.cs*:</span></span>

   [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="387f7-124">Program `using System`başlar, bu, "`System` ad alanındaki her şeyi bu dosyanın kapsamına getir" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="387f7-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="387f7-125">`System` ad alanı `Console` sınıfını içerir.</span><span class="sxs-lookup"><span data-stu-id="387f7-125">The `System` namespace includes the `Console` class.</span></span>

   <span data-ttu-id="387f7-126">Daha sonra `Hello`adlı bir ad alanı tanımlayacağız.</span><span class="sxs-lookup"><span data-stu-id="387f7-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="387f7-127">Bunu istediğiniz herhangi bir şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f7-127">You can change this to anything you want.</span></span> <span data-ttu-id="387f7-128">`Program` adlı bir sınıf, bu ad alanı içinde tanımlanır ve bağımsız değişkeni olarak bir dize dizisi alan `Main` bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="387f7-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="387f7-129">Bu dizi, derlenmiş program çağrıldığında geçirilen bağımsız değişkenlerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="387f7-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="387f7-130">Çünkü bu dizi kullanılmaz: tüm programlar "Merhaba Dünya!" yazmak</span><span class="sxs-lookup"><span data-stu-id="387f7-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="387f7-131">konsoluna gidin.</span><span class="sxs-lookup"><span data-stu-id="387f7-131">to the console.</span></span> <span data-ttu-id="387f7-132">Daha sonra, bu bağımsız değişken tarafından kullanılacak kodda değişiklik yapacağız.</span><span class="sxs-lookup"><span data-stu-id="387f7-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   <span data-ttu-id="387f7-133">`dotnet new` [`dotnet restore`](../tools/dotnet-restore.md) dolaylı olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="387f7-133">`dotnet new` calls [`dotnet restore`](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="387f7-134">Bağımlılıklar ağacını geri yüklemek için [NuGet](https://www.nuget.org/) 'e (.net Package Manager) çağrı `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="387f7-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="387f7-135">NuGet, *Hello. csproj* dosyasını analiz eder, dosyada tanımlanan bağımlılıkları indirir (veya makinenizde bir önbellekten Dallarınızla) ve örneği derlemek ve çalıştırmak için gerekli olan *obj/Project. varlıklar. JSON* dosyasını yazar.</span><span class="sxs-lookup"><span data-stu-id="387f7-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="387f7-136">SDK 'nın .NET Core 1. x sürümünü kullanıyorsanız, `dotnet new`çağrıldıktan sonra `dotnet restore` kendiniz çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="387f7-136">If you're using a .NET Core 1.x version of the SDK, you'll have to call `dotnet restore` yourself after calling `dotnet new`.</span></span>

2. `dotnet run`

   <span data-ttu-id="387f7-137">[`dotnet run`](../tools/dotnet-run.md) , derleme hedeflerinin oluşturulduğundan emin olmak için [`dotnet build`](../tools/dotnet-build.md) çağırır ve sonra hedef uygulamayı çalıştırmak için `dotnet <assembly.dll>` çağırır.</span><span class="sxs-lookup"><span data-stu-id="387f7-137">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="387f7-138">Alternatif olarak, derleme konsolu uygulamalarını çalıştırmadan kodu derlemek için de [`dotnet build`](../tools/dotnet-build.md) çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f7-138">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="387f7-139">Bu, derlenmiş bir uygulamanın Windows üzerinde `dotnet bin\Debug\netcoreapp2.1\Hello.dll` çalıştırılabilen bir DLL dosyası olarak sonuçlanır (Windows dışı sistemler için `/` kullanın).</span><span class="sxs-lookup"><span data-stu-id="387f7-139">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp2.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="387f7-140">Ayrıca, konusunda daha sonra göreceğiniz gibi uygulamanın bağımsız değişkenlerini de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f7-140">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="387f7-141">Gelişmiş bir senaryo olarak, uygulamayı, .NET Core yüklü olması gerekmeyen bir makineye dağıtılabilecek ve çalıştırılabilen, kendi kendine ait platforma özgü dosyalar kümesi olarak oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="387f7-141">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="387f7-142">Ayrıntılar için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="387f7-142">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="387f7-143">Program artırılması</span><span class="sxs-lookup"><span data-stu-id="387f7-143">Augmenting the program</span></span>

<span data-ttu-id="387f7-144">Programı bir bit olarak değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="387f7-144">Let's change the program a bit.</span></span> <span data-ttu-id="387f7-145">Fibonaccı numaraları eğlencelidir. bu nedenle, uygulamayı çalıştıran kişiyi gremek için bağımsız değişkenini kullanmaya ek olarak ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="387f7-145">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="387f7-146">*Program.cs* dosyanızın içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="387f7-146">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="387f7-147">Değişiklikleri derlemek için [`dotnet build`](../tools/dotnet-build.md) yürütün.</span><span class="sxs-lookup"><span data-stu-id="387f7-147">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="387f7-148">Uygulamaya bir parametre geçirerek programı çalıştır:</span><span class="sxs-lookup"><span data-stu-id="387f7-148">Run the program passing a parameter to the app:</span></span>

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

<span data-ttu-id="387f7-149">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="387f7-149">And that's it!</span></span>  <span data-ttu-id="387f7-150">Dilediğiniz şekilde *program.cs* yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f7-150">You can augment *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="387f7-151">Birden çok dosya ile çalışma</span><span class="sxs-lookup"><span data-stu-id="387f7-151">Working with multiple files</span></span>

<span data-ttu-id="387f7-152">Tek dosyalar basit bir tek başına programlar için uygundur, ancak daha karmaşık bir uygulama oluşturuyorsanız, muhtemelen projenizde birden fazla kaynak dosyasına sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="387f7-152">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project.</span></span>
<span data-ttu-id="387f7-153">Önceki Fibonaccı örneğini, bazı Fipriaccı değerlerini önbelleğe alarak ve bazı özyinelemeli özellikler ekleyerek oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="387f7-153">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="387f7-154">Aşağıdaki kodla *FibonacciGenerator.cs* adlı *Hello* dizininin içine yeni bir dosya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="387f7-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="387f7-155">*Program.cs* dosyanızdaki `Main` yöntemini, yeni sınıfı başlatmak ve metodunu aşağıdaki örnekte olduğu gibi çağırmak için değiştirin:</span><span class="sxs-lookup"><span data-stu-id="387f7-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="387f7-156">Değişiklikleri derlemek için [`dotnet build`](../tools/dotnet-build.md) yürütün.</span><span class="sxs-lookup"><span data-stu-id="387f7-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="387f7-157">[`dotnet run`](../tools/dotnet-run.md)yürüterek uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="387f7-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="387f7-158">Program çıktısı aşağıda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="387f7-158">The following shows the program output:</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="387f7-159">Uygulamanızı yayınlama</span><span class="sxs-lookup"><span data-stu-id="387f7-159">Publish your app</span></span>

<span data-ttu-id="387f7-160">Uygulamanızı dağıtmaya hazırladıktan sonra, _\\hata ayıklama\\netcoreapp 2.1\\hata ayıkla_ (Windows dışı sistemler için\\kullanın) konumundaki _Yayımla_ klasörünü oluşturmak için [`dotnet publish`](../tools/dotnet-publish.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="387f7-160">Once you're ready to distribute your app, use the [`dotnet publish`](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp2.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="387f7-161">Daha önce DotNet çalışma zamanını yükledikleri sürece _Publish_ klasörünün içeriğini diğer platformlara dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f7-161">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

<span data-ttu-id="387f7-162">Yayımlanmış uygulamanızı [DotNet](../tools/dotnet.md) komutuyla çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="387f7-162">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="387f7-163">Sonuç</span><span class="sxs-lookup"><span data-stu-id="387f7-163">Conclusion</span></span>

<span data-ttu-id="387f7-164">İşte bu kadar!</span><span class="sxs-lookup"><span data-stu-id="387f7-164">And that's it!</span></span> <span data-ttu-id="387f7-165">Şimdi kendi programlarınızı oluşturmak için burada öğrenilen temel kavramları kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="387f7-165">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="387f7-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="387f7-166">See also</span></span>

- [<span data-ttu-id="387f7-167">.NET Core CLI araçlarıyla projeleri düzenleme ve test etme</span><span class="sxs-lookup"><span data-stu-id="387f7-167">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
- [<span data-ttu-id="387f7-168">CLı ile .NET Core uygulamaları yayımlayın</span><span class="sxs-lookup"><span data-stu-id="387f7-168">Publish .NET Core apps with the CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="387f7-169">Uygulama dağıtımı hakkında daha fazla bilgi edinin</span><span class="sxs-lookup"><span data-stu-id="387f7-169">Learn more about app deployment</span></span>](../deploying/index.md)

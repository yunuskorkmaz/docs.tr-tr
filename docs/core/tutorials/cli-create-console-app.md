---
title: CLI kullanarak .NET Core kullanmaya başlama
description: .NET Core CLI kullanarak Windows, Linux veya macOS 'ta .NET Core ile çalışmaya başlama hakkında adım adım öğretici.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 1a691ad0c1f8dbfadd642360d7f9629a136ff3ab
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156666"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="d4889-103">.NET Core CLI kullanarak .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="d4889-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="d4889-104">Bu makalede, .NET Core CLI kullanarak Windows, Linux ve macOS üzerinde çalışan .NET Core uygulamaları geliştirmeye nasıl başlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="d4889-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="d4889-105">.NET Core CLI hakkında bilgi sahibi değilseniz, [.NET Core CLI genel bakış ' a](../tools/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d4889-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4889-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="d4889-106">Prerequisites</span></span>

- <span data-ttu-id="d4889-107">[.NET Core SDK 3,1](https://dotnet.microsoft.com/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="d4889-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="d4889-108">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d4889-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="d4889-109">Merhaba, konsol uygulaması!</span><span class="sxs-lookup"><span data-stu-id="d4889-109">Hello, Console App!</span></span>

<span data-ttu-id="d4889-110">Örnek kodu DotNet/Samples GitHub deposundan [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) .</span><span class="sxs-lookup"><span data-stu-id="d4889-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="d4889-111">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="d4889-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="d4889-112">Bir komut istemi açın ve *Hello*adlı bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d4889-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="d4889-113">Oluşturduğunuz klasöre gidin ve aşağıdakini yazın.</span><span class="sxs-lookup"><span data-stu-id="d4889-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="d4889-114">Hızlı bir yol açalım:</span><span class="sxs-lookup"><span data-stu-id="d4889-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="d4889-115">[DotNet New](../tools/dotnet-new.md) , bir konsol uygulaması oluşturmak için gereken bağımlılıklara sahip bir güncel *Hello. csproj* proje dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4889-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="d4889-116">Ayrıca, uygulamanın giriş noktasını içeren temel bir dosya olan bir *program.cs*oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4889-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="d4889-117">*Merhaba. csproj*:</span><span class="sxs-lookup"><span data-stu-id="d4889-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]

    <span data-ttu-id="d4889-118">Proje dosyası, bağımlılıkları geri yüklemek ve programı derlemek için gereken her şeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4889-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="d4889-119">`<OutputType>` öğesi, bir konsol uygulaması diğer bir deyişle yürütülebilir bir dosya oluşturduğumuz olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4889-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="d4889-120">`<TargetFramework>` öğesi hangi .NET uygulamasını hedefliyoruz belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4889-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="d4889-121">Gelişmiş bir senaryoda, birden çok hedef çerçeve belirtebilir ve tek bir işlemde bunların tümüne derleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4889-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="d4889-122">Bu öğreticide yalnızca .NET Core 3,1 için derleme yapacağız.</span><span class="sxs-lookup"><span data-stu-id="d4889-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="d4889-123">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="d4889-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]

    <span data-ttu-id="d4889-124">Program `using System`başlar, bu, "`System` ad alanındaki her şeyi bu dosyanın kapsamına getir" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d4889-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="d4889-125">`System` ad alanı `Console` sınıfını içerir.</span><span class="sxs-lookup"><span data-stu-id="d4889-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="d4889-126">Daha sonra `Hello`adlı bir ad alanı tanımlayacağız.</span><span class="sxs-lookup"><span data-stu-id="d4889-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="d4889-127">Bunu istediğiniz herhangi bir şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4889-127">You can change this to anything you want.</span></span> <span data-ttu-id="d4889-128">`Program` adlı bir sınıf, `args`adlı dizelerin dizisini alan `Main` yöntemi ile bu ad alanı içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d4889-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="d4889-129">Bu dizi, program çalıştırıldığında geçirilen bağımsız değişkenlerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="d4889-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="d4889-130">Çünkü bu dizi kullanılmaz ve program yalnızca "Merhaba Dünya!" metnini yazar</span><span class="sxs-lookup"><span data-stu-id="d4889-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="d4889-131">konsoluna gidin.</span><span class="sxs-lookup"><span data-stu-id="d4889-131">to the console.</span></span> <span data-ttu-id="d4889-132">Daha sonra, bu bağımsız değişken tarafından kullanılacak kodda değişiklik yapacağız.</span><span class="sxs-lookup"><span data-stu-id="d4889-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="d4889-133">`dotnet new` [DotNet restore](../tools/dotnet-restore.md) dolaylı olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="d4889-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="d4889-134">Bağımlılıklar ağacını geri yüklemek için [NuGet](https://www.nuget.org/) 'e (.net Package Manager) çağrı `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="d4889-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="d4889-135">NuGet, *Hello. csproj* dosyasını analiz eder, dosyada tanımlanan bağımlılıkları indirir (veya makinenizde bir önbellekten Dallarınızla) ve örneği derlemek ve çalıştırmak için gerekli olan *obj/Project. varlıklar. JSON* dosyasını yazar.</span><span class="sxs-lookup"><span data-stu-id="d4889-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="d4889-136">[DotNet Run](../tools/dotnet-run.md) , derleme hedeflerinin oluşturulduğundan emin olmak için [DotNet derlemesini](../tools/dotnet-build.md) çağırır ve sonra hedef uygulamayı çalıştırmak için `dotnet <assembly.dll>` çağırır.</span><span class="sxs-lookup"><span data-stu-id="d4889-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="d4889-137">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d4889-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="d4889-138">Alternatif olarak, derleme konsolu uygulamalarını çalıştırmadan kodu derlemek için `dotnet build` de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4889-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="d4889-139">Bu, bir DLL dosyası olarak proje adına bağlı olarak derlenmiş bir uygulama ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="d4889-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="d4889-140">Bu durumda, oluşturulan dosya *Hello. dll*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d4889-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="d4889-141">Bu uygulama, Windows üzerinde `dotnet bin\Debug\netcoreapp3.1\Hello.dll` çalıştırılabilir (Windows dışı sistemler için `/` kullanın).</span><span class="sxs-lookup"><span data-stu-id="d4889-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="d4889-142">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d4889-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="d4889-143">Uygulama derlendiğinde, `Hello.dll`birlikte işletim sistemine özgü bir yürütülebilir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d4889-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="d4889-144">Windows 'da bu `Hello.exe`olur; Linux veya macOS üzerinde bu `hello`.</span><span class="sxs-lookup"><span data-stu-id="d4889-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="d4889-145">Yukarıdaki örnekte, dosya `Hello.exe` veya `Hello`ile adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d4889-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="d4889-146">Bu yürütülebilir dosyayı doğrudan çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4889-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="d4889-147">Programı değiştirme</span><span class="sxs-lookup"><span data-stu-id="d4889-147">Modify the program</span></span>

<span data-ttu-id="d4889-148">Programı bir bit olarak değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="d4889-148">Let's change the program a bit.</span></span> <span data-ttu-id="d4889-149">Fibonaccı numaraları eğlencelidir. bu nedenle, uygulamayı çalıştıran kişiyi almak için bağımsız değişkenini de kullanarak ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="d4889-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="d4889-150">*Program.cs* dosyanızın içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d4889-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. <span data-ttu-id="d4889-151">Değişiklikleri derlemek için [DotNet derlemesini](../tools/dotnet-build.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4889-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="d4889-152">Uygulamaya bir parametre geçirerek programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4889-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="d4889-153">Bir uygulamayı çalıştırmak için `dotnet` komutunu kullandığınızda sonuna `--` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d4889-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="d4889-154">`--` sağına herhangi bir şey, uygulamaya parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d4889-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="d4889-155">Aşağıdaki örnekte `John` değeri uygulamaya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="d4889-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="d4889-156">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d4889-156">You get the following output.</span></span>

    ```console
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

<span data-ttu-id="d4889-157">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="d4889-157">And that's it!</span></span> <span data-ttu-id="d4889-158">Dilediğiniz gibi *program.cs* değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4889-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="d4889-159">Birden çok dosya ile çalışma</span><span class="sxs-lookup"><span data-stu-id="d4889-159">Working with multiple files</span></span>

<span data-ttu-id="d4889-160">Tek dosyalar basit bir tek başına programlar için uygundur, ancak daha karmaşık bir uygulama oluşturuyorsanız, muhtemelen projenizde birden çok kod dosyasına sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="d4889-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="d4889-161">Önceki Fibonaccı örneğini, bazı Fipriaccı değerlerini önbelleğe alarak ve bazı özyinelemeli özellikler ekleyerek oluşturalım.</span><span class="sxs-lookup"><span data-stu-id="d4889-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="d4889-162">Aşağıdaki kodla *FibonacciGenerator.cs* adlı *Hello* dizininin içine yeni bir dosya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="d4889-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. <span data-ttu-id="d4889-163">*Program.cs* dosyanızdaki `Main` yöntemini, yeni sınıfı başlatmak ve metodunu aşağıdaki örnekte olduğu gibi çağırmak için değiştirin:</span><span class="sxs-lookup"><span data-stu-id="d4889-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. <span data-ttu-id="d4889-164">Değişiklikleri derlemek için [DotNet derlemesini](../tools/dotnet-build.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4889-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="d4889-165">[DotNet çalıştırmasını](../tools/dotnet-run.md)yürüterek uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d4889-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="d4889-166">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d4889-166">You get the following output.</span></span>

    ```console
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

## <a name="publish-your-app"></a><span data-ttu-id="d4889-167">Uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="d4889-167">Publish your app</span></span>

<span data-ttu-id="d4889-168">Uygulamanızı dağıtmaya hazırladıktan sonra, _\\,\\netcoreapp 3.1\\hata ayıkla_ (Windows dışı sistemler için\\kullanın) konumundaki _Yayımla_ klasörünü oluşturmak için [DotNet Publish](../tools/dotnet-publish.md) komutunu kullanın.`/`</span><span class="sxs-lookup"><span data-stu-id="d4889-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="d4889-169">Daha önce DotNet çalışma zamanını yükledikleri sürece _Publish_ klasörünün içeriğini diğer platformlara dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4889-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="d4889-170">Aşağıdakine benzer bir çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d4889-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="d4889-171">Yukarıdaki çıkış, geçerli klasörünüze ve işletim sisteminize göre farklılık gösterebilir, ancak çıktının benzer olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d4889-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="d4889-172">Yayımlanmış uygulamanızı [DotNet](../tools/dotnet.md) komutuyla çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d4889-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="d4889-173">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="d4889-173">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="d4889-174">Bu makalenin başlangıcında belirtildiği gibi, `Hello.dll`birlikte işletim sistemine özgü bir yürütülebilir dosya oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d4889-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="d4889-175">Windows 'da bu `Hello.exe`olur; Linux veya macOS üzerinde bu `hello`.</span><span class="sxs-lookup"><span data-stu-id="d4889-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="d4889-176">Yukarıdaki örnekte, dosya `Hello.exe` veya `Hello`ile adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d4889-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="d4889-177">Bu yayınlanan yürütülebilir dosyayı doğrudan çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4889-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="d4889-178">Sonuç</span><span class="sxs-lookup"><span data-stu-id="d4889-178">Conclusion</span></span>

<span data-ttu-id="d4889-179">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="d4889-179">And that's it!</span></span> <span data-ttu-id="d4889-180">Şimdi kendi programlarınızı oluşturmak için burada öğrenilen temel kavramları kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4889-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4889-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4889-181">See also</span></span>

- [<span data-ttu-id="d4889-182">.NET Core CLI projeleri düzenleme ve test etme</span><span class="sxs-lookup"><span data-stu-id="d4889-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="d4889-183">.NET Core CLI .NET Core uygulamaları yayımlayın</span><span class="sxs-lookup"><span data-stu-id="d4889-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="d4889-184">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="d4889-184">.NET Core application deployment</span></span>](../deploying/index.md)

---
title: CLI kullanarak .NET Core kullanmaya başlama
description: .NET Core CLI'yi kullanarak Windows, Linux veya macOS'ta .NET Core ile nasıl başlaşmak gerektiğini gösteren adım adım bir öğretici.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240863"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="58313-103">.NET Core CLI'yi kullanarak .NET Core ile başlayın</span><span class="sxs-lookup"><span data-stu-id="58313-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="58313-104">Bu makalede, .NET Core CLI'yi kullanarak Windows, Linux ve macOS'ta çalışan .NET Core uygulamalarını geliştirmeye nasıl başlayacağınızı gösterecektir.</span><span class="sxs-lookup"><span data-stu-id="58313-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="58313-105">.NET Core CLI'ye aşina [değilseniz,.NET Core CLI genel](../tools/index.md)bakış'ına bakın.</span><span class="sxs-lookup"><span data-stu-id="58313-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58313-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="58313-106">Prerequisites</span></span>

- <span data-ttu-id="58313-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="58313-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="58313-108">Tercih ettiğiniz bir metin veya kod düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="58313-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="58313-109">Merhaba, Konsol Uygulaması!</span><span class="sxs-lookup"><span data-stu-id="58313-109">Hello, Console App!</span></span>

<span data-ttu-id="58313-110">Örnek kodu dotnet/samples GitHub deposundan [görüntüleyebilir veya indirebilirsiniz.](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild)</span><span class="sxs-lookup"><span data-stu-id="58313-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="58313-111">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="58313-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="58313-112">Komut istemini açın ve *Merhaba*adlı bir klasör oluşturun.</span><span class="sxs-lookup"><span data-stu-id="58313-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="58313-113">Oluşturduğunuz klasöre gidin ve aşağıdakileri yazın.</span><span class="sxs-lookup"><span data-stu-id="58313-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="58313-114">Hızlı bir gözden geçirme yapalım:</span><span class="sxs-lookup"><span data-stu-id="58313-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="58313-115">[dotnet yeni](../tools/dotnet-new.md) bir konsol uygulaması oluşturmak için gerekli bağımlılıkları ile güncel bir *Hello.csproj* proje dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58313-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="58313-116">Ayrıca, uygulama için giriş noktasını içeren temel bir dosya olan *Program.cs*oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58313-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="58313-117">*Merhaba.csproj*:</span><span class="sxs-lookup"><span data-stu-id="58313-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="58313-118">Proje dosyası, bağımlılıkları geri yüklemek ve programı oluşturmak için gereken her şeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="58313-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="58313-119">Öğe, `<OutputType>` bir yürütülebilir, başka bir deyişle bir konsol uygulaması oluşturuyoruz belirtir.</span><span class="sxs-lookup"><span data-stu-id="58313-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="58313-120">Öğe, `<TargetFramework>` hedeflediğimiz .NET uygulamasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="58313-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="58313-121">Gelişmiş bir senaryoda, birden çok hedef çerçevesi belirtebilir ve tek bir işlemdeki herkese oluşturun.</span><span class="sxs-lookup"><span data-stu-id="58313-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="58313-122">Bu eğitimde, sadece .NET Core 3.1 için oluşturmaya devam edeceğiz.</span><span class="sxs-lookup"><span data-stu-id="58313-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="58313-123">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="58313-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="58313-124">Program `using System`, `System` "bu dosya için kapsamına ad alanında her şeyi getirmek" anlamına gelir başlar.</span><span class="sxs-lookup"><span data-stu-id="58313-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="58313-125">Ad `System` alanı `Console` sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="58313-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="58313-126">Daha sonra bir ad `Hello`alanı olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="58313-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="58313-127">Bunu istediğin şeyle değiştirebilirsin.</span><span class="sxs-lookup"><span data-stu-id="58313-127">You can change this to anything you want.</span></span> <span data-ttu-id="58313-128">Adlı `Program` bir sınıf, adlı `Main` `args`dizeleri bir dizi alan bir yöntem ile, bu ad alanı içinde tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="58313-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="58313-129">Bu dizi, program çalıştırıldığında geçirilen bağımsız değişkenlerin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="58313-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="58313-130">Olduğu gibi, bu dizi kullanılmaz ve program sadece metin "Merhaba Dünya yazıyor!"</span><span class="sxs-lookup"><span data-stu-id="58313-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="58313-131">metnini görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="58313-131">to the console.</span></span> <span data-ttu-id="58313-132">Daha sonra, bu bağımsız değişkenden yararlanacak kodda değişiklikler yapacağız.</span><span class="sxs-lookup"><span data-stu-id="58313-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="58313-133">`dotnet new`[dotnet geri yükleme](../tools/dotnet-restore.md) çağırır örtülü olarak.</span><span class="sxs-lookup"><span data-stu-id="58313-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="58313-134">`dotnet restore`bağımlılıklar ağacını geri yüklemek için [NuGet'e](https://www.nuget.org/) (.NET paket yöneticisi) çağrır.</span><span class="sxs-lookup"><span data-stu-id="58313-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="58313-135">NuGet *Hello.csproj* dosyasını analiz eder, dosyada tanımlanan bağımlılıkları karşıdan yükler (veya makinenizdeki bir önbellekten yakalar) ve örneği derlemek ve çalıştırmak için gerekli olan *obj/project.assets.json* dosyasını yazar.</span><span class="sxs-lookup"><span data-stu-id="58313-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="58313-136">[dotnet,](../tools/dotnet-run.md) yapı hedeflerinin inşa edildiğinden emin olmak için [dotnet yapılı](../tools/dotnet-build.md) çağrıları çalıştırır ve ardından hedef uygulamayı çalıştırmak için çağrılar da yapar. `dotnet <assembly.dll>`</span><span class="sxs-lookup"><span data-stu-id="58313-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="58313-137">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="58313-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="58313-138">Alternatif olarak, yapı `dotnet build` konsolu uygulamalarını çalıştırmadan kodu derlemek için de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58313-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="58313-139">Bu, projenin adını temel alan bir DLL dosyası olarak derlenmiş bir uygulamayla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="58313-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="58313-140">Bu durumda, oluşturulan dosya *Hello.dll*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="58313-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="58313-141">Bu uygulama `dotnet bin\Debug\netcoreapp3.1\Hello.dll` Windows'da çalıştırılabilir `/` (Windows olmayan sistemler için kullanın).</span><span class="sxs-lookup"><span data-stu-id="58313-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="58313-142">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="58313-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="58313-143">Uygulama derlendiğinde, işletim sistemine özgü bir çalıştırılabilir `Hello.dll`</span><span class="sxs-lookup"><span data-stu-id="58313-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="58313-144">Windows'da, bu `Hello.exe`olurdu; Linux veya macOS, bu `hello`olurdu .</span><span class="sxs-lookup"><span data-stu-id="58313-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="58313-145">Yukarıdaki örnekte, dosya ile `Hello.exe` adlandırılır `Hello`veya .</span><span class="sxs-lookup"><span data-stu-id="58313-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="58313-146">Bu çalıştırılabilir doğrudan çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58313-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="58313-147">Programı değiştirme</span><span class="sxs-lookup"><span data-stu-id="58313-147">Modify the program</span></span>

<span data-ttu-id="58313-148">Programı biraz değiştirelim.</span><span class="sxs-lookup"><span data-stu-id="58313-148">Let's change the program a bit.</span></span> <span data-ttu-id="58313-149">Fibonacci numaraları eğlenceli, bu yüzden bunu ekleyelim ve ayrıca uygulamayı çalıştıran kişiyi karşılamak için argümanı kullanalım.</span><span class="sxs-lookup"><span data-stu-id="58313-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="58313-150">*Program.cs* dosyanızın içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="58313-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="58313-151">Değişiklikleri derlemek için [dotnet yapısını](../tools/dotnet-build.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="58313-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="58313-152">Uygulamaya bir parametre geçen programı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="58313-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="58313-153">Bir uygulamayı `dotnet` çalıştırmak için komutu `--` kullandığınızda, sonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="58313-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="58313-154">Sağdaki her `--` şey uygulamaya parametre olarak geçirilecektir.</span><span class="sxs-lookup"><span data-stu-id="58313-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="58313-155">Aşağıdaki örnekte, değer `John` uygulamaya aktarılır.</span><span class="sxs-lookup"><span data-stu-id="58313-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="58313-156">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="58313-156">You get the following output.</span></span>

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

<span data-ttu-id="58313-157">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="58313-157">And that's it!</span></span> <span data-ttu-id="58313-158">*İstediğiniz Program.cs* değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58313-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="58313-159">Birden çok dosyayla çalışma</span><span class="sxs-lookup"><span data-stu-id="58313-159">Working with multiple files</span></span>

<span data-ttu-id="58313-160">Tek dosyalar basit tek seferlik programlar için iyidir, ancak daha karmaşık bir uygulama oluşturuyorsanız, büyük olasılıkla projenizde birden çok kod dosyanız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="58313-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="58313-161">Bazı Fibonacci değerlerini önbelleğe alarak önceki Fibonacci örneğini oluşturalım ve bazı özyinelemeli özellikler ekleyelim.</span><span class="sxs-lookup"><span data-stu-id="58313-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="58313-162">Aşağıdaki kodla *FibonacciGenerator.cs* adlı *Merhaba* dizininin içine yeni bir dosya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="58313-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="58313-163">Yeni `Main` sınıfı anında açmak ve yöntemiaşağıdaki örnekte olduğu gibi çağırmak için *Program.cs* dosyanızdaki yöntemi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="58313-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="58313-164">Değişiklikleri derlemek için [dotnet yapısını](../tools/dotnet-build.md) çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="58313-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="58313-165">[dotnet çalıştırarak](../tools/dotnet-run.md)uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="58313-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="58313-166">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="58313-166">You get the following output.</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="58313-167">Uygulamanızı yayımlama</span><span class="sxs-lookup"><span data-stu-id="58313-167">Publish your app</span></span>

<span data-ttu-id="58313-168">Uygulamanızı dağıtmaya hazır olduğunuzda, _bin\\debug\\netcoreapp3.1\\publish\\ _ 'de _yayımlama_ klasörünü oluşturmak için [dotnet yayımlama](../tools/dotnet-publish.md) komutunu kullanın (Windows dışı sistemler için kullanın). `/`</span><span class="sxs-lookup"><span data-stu-id="58313-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="58313-169">Dotnet çalışma süresini yükledikleri sürece _yayımlama_ klasörünün içeriğini diğer platformlara dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58313-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="58313-170">Aşağıdakine benzer çıktı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="58313-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="58313-171">Yukarıdaki çıktı geçerli klasörünüze ve işletim sisteminize bağlı olarak farklılık gösterebilir, ancak çıktı benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58313-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="58313-172">Yayınlanan uygulamanızı [dotnet](../tools/dotnet.md) komutu ile çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58313-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="58313-173">Aşağıdaki çıktıyı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="58313-173">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="58313-174">Bu makalenin başında belirtildiği gibi, bir işletim sistemi özel çalıştırılabilir `Hello.dll`ile birlikte oluşturuldu .</span><span class="sxs-lookup"><span data-stu-id="58313-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="58313-175">Windows'da, bu `Hello.exe`olurdu; Linux veya macOS, bu `hello`olurdu .</span><span class="sxs-lookup"><span data-stu-id="58313-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="58313-176">Yukarıdaki örnekte, dosya ile `Hello.exe` adlandırılır `Hello`veya .</span><span class="sxs-lookup"><span data-stu-id="58313-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="58313-177">Bu yayımlanabilir çalıştırılabilir çalıştırAbilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58313-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="58313-178">Sonuç</span><span class="sxs-lookup"><span data-stu-id="58313-178">Conclusion</span></span>

<span data-ttu-id="58313-179">Hepsi bu!</span><span class="sxs-lookup"><span data-stu-id="58313-179">And that's it!</span></span> <span data-ttu-id="58313-180">Şimdi, kendi programlarınızı oluşturmak için burada öğrenilen temel kavramları kullanmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58313-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="58313-181">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58313-181">See also</span></span>

- [<span data-ttu-id="58313-182">.NET Core CLI ile projelerin düzenlenmesi ve test edilmesi</span><span class="sxs-lookup"><span data-stu-id="58313-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="58313-183">.NET Core CLI ile .NET Core uygulamalarını yayımla</span><span class="sxs-lookup"><span data-stu-id="58313-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="58313-184">.NET Core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="58313-184">.NET Core application deployment</span></span>](../deploying/index.md)

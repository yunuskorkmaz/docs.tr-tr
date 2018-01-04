---
title: "MacOS üzerinde .NET Core'u kullanmaya başlama"
description: "Bu belge, .NET Core Visual Studio kod kullanarak bir çözüm oluşturmak için iş akışı ve adımları sağlar."
keywords: .NET, .NET core, Mac, macOS, Visual Studio Code
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
ms.workload: dotnetcore
ms.openlocfilehash: 5a8f1fca7623763d43b977d0cc44396de249c62e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="getting-started-with-net-core-on-macos"></a><span data-ttu-id="0d742-104">MacOS üzerinde .NET Core'u kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="0d742-104">Getting started with .NET Core on macOS</span></span>

<span data-ttu-id="0d742-105">Bu belge macOS .NET Core çözüm oluşturmak için iş akışı ve adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d742-105">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="0d742-106">Projeleri, birim testleri oluşturma, hata ayıklama araçlarını kullanın ve üçüncü taraf kitaplıkları aracılığıyla dahil öğrenin [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="0d742-106">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="0d742-107">Bu makalede kullanan [Visual Studio Code](http://code.visualstudio.com) macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0d742-107">This article uses [Visual Studio Code](http://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0d742-108">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0d742-108">Prerequisites</span></span>

<span data-ttu-id="0d742-109">Yükleme [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="0d742-109">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="0d742-110">.NET Core SDK .NET Core framework ve çalışma zamanı en son sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="0d742-110">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="0d742-111">Yükleme [Visual Studio Code](http://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="0d742-111">Install [Visual Studio Code](http://code.visualstudio.com).</span></span> <span data-ttu-id="0d742-112">Bu makalede sürecinde, Visual Studio .NET Core geliştirme geliştirmek uzantıları deneyimi kodu da yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0d742-112">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="0d742-113">Visual Studio Code açarak ve tuşuna basarak Visual Studio kod C# uzantısını yüklemeniz <kbd>F1</kbd> Visual Studio Code paletini açmak için.</span><span class="sxs-lookup"><span data-stu-id="0d742-113">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="0d742-114">Tür **ext yüklemek** uzantılarının listesini görmek için.</span><span class="sxs-lookup"><span data-stu-id="0d742-114">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="0d742-115">C# uzantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="0d742-115">Select the C# extension.</span></span> <span data-ttu-id="0d742-116">Uzantıyı etkinleştirmek için Visual Studio Code yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="0d742-116">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="0d742-117">Daha fazla bilgi için bkz: [Visual Studio kod C# uzantısı belgelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="0d742-117">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="getting-started"></a><span data-ttu-id="0d742-118">Başlarken</span><span class="sxs-lookup"><span data-stu-id="0d742-118">Getting started</span></span>

<span data-ttu-id="0d742-119">Bu öğreticide, üç projeleri oluşturma: bir kitaplık projesine testleri kitaplığı proje ve bir konsol uygulaması yapar kitaplığını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0d742-119">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="0d742-120">Yapabilecekleriniz [görüntülemek veya kaynak indirme](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) github'da dotnet/docs deposunda Bu konu için.</span><span class="sxs-lookup"><span data-stu-id="0d742-120">You can [view or download the source](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) for this topic at the dotnet/docs repository on GitHub.</span></span> <span data-ttu-id="0d742-121">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="0d742-121">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="0d742-122">Visual Studio Code başlatın.</span><span class="sxs-lookup"><span data-stu-id="0d742-122">Start Visual Studio Code.</span></span> <span data-ttu-id="0d742-123">Tuşuna <kbd>Ctrl</kbd> + <kbd> \\` </kbd> (ters tırnak veya backtick karakter) ya da seçin **Görünüm > tümleşik Terminal** katıştırılmış açmak için menüden Visual Studio Code terminale.</span><span class="sxs-lookup"><span data-stu-id="0d742-123">Press <kbd>Ctrl</kbd>+<kbd>\\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="0d742-124">Dış bir kabuk Gezgini ile yine de açabilirsiniz **bir komut istemi açın** komutu (**içinde Terminali açın** Mac veya Linux) dışında Visual Studio Code çalışmayı tercih ederseniz.</span><span class="sxs-lookup"><span data-stu-id="0d742-124">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="0d742-125">Bir veya daha fazla .NET Core projeleri için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="0d742-125">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="0d742-126">Terminale oluşturma bir *altın* klasörü ve klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="0d742-126">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="0d742-127">Bu klasör çözümünüzü köküdür.</span><span class="sxs-lookup"><span data-stu-id="0d742-127">This folder is the root of your solution.</span></span> <span data-ttu-id="0d742-128">Çalıştırma [ `dotnet new` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için komutu *golden.sln*:</span><span class="sxs-lookup"><span data-stu-id="0d742-128">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="0d742-129">Gelen *altın* klasörü, iki dosyalar oluşturur, bir kitaplık projesi oluşturmak için aşağıdaki komutu yürütün*library.csproj* ve *Class1.cs*, içinde*Kitaplığı* klasörü:</span><span class="sxs-lookup"><span data-stu-id="0d742-129">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="0d742-130">Yürütme [ `dotnet sln` ](../tools/dotnet-sln.md) yeni oluşturulan eklemek için komutu *library.csproj* çözüme proje:</span><span class="sxs-lookup"><span data-stu-id="0d742-130">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="0d742-131">*Library.csproj* dosya, aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="0d742-131">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="0d742-132">Bizim kitaplığı yöntemleri seri hale getirmek ve nesneleri JSON biçiminde seri durumdan.</span><span class="sxs-lookup"><span data-stu-id="0d742-132">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="0d742-133">JSON seri hale getirme ve seri durumdan çıkarma desteklemek için bir başvuru ekleyin `Newtonsoft.Json` NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="0d742-133">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="0d742-134">`dotnet add` Komut bir projesine yeni öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="0d742-134">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="0d742-135">NuGet paketine başvuru eklemek için kullanın [ `dotnet add package` ](../tools/dotnet-add-package.md) komut ve paketinin adını belirtin:</span><span class="sxs-lookup"><span data-stu-id="0d742-135">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="0d742-136">Bu ekler `Newtonsoft.Json` ve bağımlılıklarını kitaplığı projesine.</span><span class="sxs-lookup"><span data-stu-id="0d742-136">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="0d742-137">Alternatif olarak, el ile düzenleme *library.csproj* dosya ve aşağıdaki düğüm ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0d742-137">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="0d742-138">Yürütme [ `dotnet restore` ](../tools/dotnet-restore.md), ([nota bakın](#dotnet-restore-note)) bağımlılıkları yükler ve oluşturur bir *obj* klasöre *Kitaplığı* üç dahil olmak üzere, dosyaları bir *project.assets.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="0d742-138">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="0d742-139">İçinde *Kitaplığı* klasörü, dosyayı yeniden adlandırın *Class1.cs* için *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="0d742-139">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="0d742-140">Kod aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0d742-140">Replace the code with the following:</span></span>

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

<span data-ttu-id="0d742-141">`Thing` Sınıfı içeren bir genel yöntem `Get`, iki toplamını numaraları ancak bunu toplamı bir dizeye dönüştürme ve tamsayı seri durumdan desteklemez döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d742-141">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="0d742-142">Bu kullanır modern C# özellikleri, bir dizi gibi [ `using static` yönergeleri](../../csharp/language-reference/keywords/using-static.md), [ifade bodied üyeleri](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), ve [Ara değerli dizeler](../../csharp/language-reference/keywords/interpolated-strings.md).</span><span class="sxs-lookup"><span data-stu-id="0d742-142">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [interpolated strings](../../csharp/language-reference/keywords/interpolated-strings.md).</span></span>

<span data-ttu-id="0d742-143">Kitaplıkla yapı [ `dotnet build` ](../tools/dotnet-build.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="0d742-143">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="0d742-144">Bu üreten bir *library.dll* altında dosya *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="0d742-144">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="0d742-145">Testi projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d742-145">Create the test project</span></span>

<span data-ttu-id="0d742-146">Kitaplık için bir test projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0d742-146">Build a test project for the library.</span></span> <span data-ttu-id="0d742-147">Gelen *altın* klasörü, yeni bir test projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0d742-147">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="0d742-148">Oluşturduğunuz test projesinin çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0d742-148">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="0d742-149">Böylece derleyici bulmak ve kitaplığı projesi kullanın, önceki bölümde oluşturduğunuz kitaplığı proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0d742-149">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="0d742-150">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="0d742-150">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="0d742-151">Alternatif olarak, el ile düzenleme *test library.csproj* dosya ve aşağıdaki düğüm ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0d742-151">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="0d742-152">Bağımlılıkları düzgün yapılandırılmadığından, kitaplık için testleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0d742-152">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="0d742-153">Açık *UnitTest1.cs* ve içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0d742-153">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="0d742-154">Değerin 42 19 + 23 (ya da 42) eşit değil assert Not ilk oluşturduğunuzda birim testi (`Assert.NotEqual`), hangi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0d742-154">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="0d742-155">Birim testleri oluşturmanın önemli bir adım, mantığını onaylamak ilk kez başarısız test oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0d742-155">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="0d742-156">Gelen *altın* klasörü, aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0d742-156">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="0d742-157">Bu komutlar bağımlılıkları geri yükleme, bunları oluşturmak ve xUnit etkinleştirmek için tüm projeleri test Çalıştırıcısı testleri çalıştırmak için özyinelemeli bulma olur.</span><span class="sxs-lookup"><span data-stu-id="0d742-157">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="0d742-158">Beklediğiniz gibi tek bir test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0d742-158">The single test fails, as you expect.</span></span>

<span data-ttu-id="0d742-159">Düzen *UnitTest1.cs* dosya ve gelen onaylama değiştirme `Assert.NotEqual` için `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="0d742-159">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="0d742-160">Aşağıdaki komutu yürütün *altın* klasör bu süre geçtikten testi yeniden çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="0d742-160">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="0d742-161">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d742-161">Create the console app</span></span>

<span data-ttu-id="0d742-162">Aşağıdaki adımlar üzerinde oluşturduğunuz konsol uygulaması bir bağımlılık kitaplığı projeye daha önce oluşturduğunuz ve çalıştırıldığında, kendi kitaplığı yöntemini çağırır alır.</span><span class="sxs-lookup"><span data-stu-id="0d742-162">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="0d742-163">Bu geliştirme desenini kullanarak, birden çok proje için yeniden kullanılabilir kitaplıkları oluşturma bakın.</span><span class="sxs-lookup"><span data-stu-id="0d742-163">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="0d742-164">Yeni bir konsol uygulamasından oluşturma *altın* klasörü:</span><span class="sxs-lookup"><span data-stu-id="0d742-164">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="0d742-165">Konsol uygulama projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0d742-165">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="0d742-166">Kitaplıkta çalıştırarak bağımlılığa yol `dotnet add reference` komutu:</span><span class="sxs-lookup"><span data-stu-id="0d742-166">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="0d742-167">Çalıştırma `dotnet restore` ([bkz. Not](#dotnet-restore-note)) çözümde üç proje bağımlılıkları geri yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="0d742-167">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="0d742-168">Açık *Program.cs* ve içeriğini değiştirme `Main` aşağıdaki satırı yöntemiyle:</span><span class="sxs-lookup"><span data-stu-id="0d742-168">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="0d742-169">İki eklemek `using` üst kısmındaki yönergeleri *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="0d742-169">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="0d742-170">Aşağıdaki yürütme `dotnet run` yürütülebilir, where çalıştırılacak komutu `-p` için seçenek `dotnet run` ana uygulaması için projeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d742-170">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="0d742-171">Uygulama "yanıt 42 olduğu" dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0d742-171">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="0d742-172">Uygulamada hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0d742-172">Debug the application</span></span>

<span data-ttu-id="0d742-173">Konumunda bir kesme noktası belirleyerek `WriteLine` deyiminde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0d742-173">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="0d742-174">Her iki basarak bunu <kbd>F9</kbd> anahtar İmleç üzerinden olduğunda `WriteLine` satır veya fareyi kesme noktası ayarlamak istediğiniz sol kenar boşluğunda satırında tıklayarak.</span><span class="sxs-lookup"><span data-stu-id="0d742-174">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="0d742-175">Kırmızı bir daire kod satırı kenar görünür.</span><span class="sxs-lookup"><span data-stu-id="0d742-175">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="0d742-176">Kod yürütmeyi kesme ulaşıldığında durdurur *önce* kesme çizgi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0d742-176">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="0d742-177">Visual Studio Code araç çubuğunda, hata ayıklama simgesini seçerek hata ayıklayıcı sekmesini açın seçme **Görünüm > hata ayıklama** menü çubuğunda veya klavye kısayolunu kullanarak <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="0d742-177">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Visual Studio kod hata ayıklayıcı](./media/using-on-macos/vscodedebugger.png)

<span data-ttu-id="0d742-179">Hata ayıklayıcı altında uygulamayı başlatmak için YÜRÜT düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="0d742-179">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="0d742-180">Uygulama yürütme başlar ve burada durdurur kesme noktasına çalışır.</span><span class="sxs-lookup"><span data-stu-id="0d742-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="0d742-181">Adımla `Get` yöntemi ve doğru bağımsız değişken geçirilen emin olun.</span><span class="sxs-lookup"><span data-stu-id="0d742-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="0d742-182">Yanıt 42 olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="0d742-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
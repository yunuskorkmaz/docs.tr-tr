---
title: "Öğretici: Visual Studio Code kullanarak macOS 'ta .NET Core çözümü oluşturma"
description: Bu belge, Visual Studio Code kullanarak bir .NET Core çözümü oluşturmak için adımlar ve iş akışı sağlar.
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: 022afd99c6d36d7a60ac40f3f27ba073c5470bd2
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082808"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="0110e-103">Öğretici: Visual Studio Code kullanarak macOS 'ta .NET Core çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="0110e-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="0110e-104">Bu belge, macOS için .NET Core çözümü oluşturmaya yönelik adımları ve iş akışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0110e-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="0110e-105">Projeler, birim testleri oluşturma, hata ayıklama araçlarını kullanma ve [NuGet](https://www.nuget.org/)aracılığıyla üçüncü taraf kitaplıklarını birleştirme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="0110e-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="0110e-106">Bu makale macOS üzerinde [Visual Studio Code](https://code.visualstudio.com) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0110e-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0110e-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0110e-107">Prerequisites</span></span>

<span data-ttu-id="0110e-108">[.NET Core SDK](https://dotnet.microsoft.com/download)'i yükler.</span><span class="sxs-lookup"><span data-stu-id="0110e-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="0110e-109">.NET Core SDK .NET Core Framework ve çalışma zamanının en son sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="0110e-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="0110e-110">[Visual Studio Code](https://code.visualstudio.com)'i yükler.</span><span class="sxs-lookup"><span data-stu-id="0110e-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="0110e-111">Bu makalenin kursu sırasında, .NET Core geliştirme deneyimini geliştiren Visual Studio Code uzantıları da yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="0110e-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="0110e-112">Visual Studio Code açıp C# <kbd>F1</kbd> tuşuna basarak Visual Studio Code uzantısını yükleyip Visual Studio Code paleti açın.</span><span class="sxs-lookup"><span data-stu-id="0110e-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="0110e-113">Uzantı listesini görmek için **EXT Install** yazın.</span><span class="sxs-lookup"><span data-stu-id="0110e-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="0110e-114">C# Uzantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="0110e-114">Select the C# extension.</span></span> <span data-ttu-id="0110e-115">Uzantıyı etkinleştirmek için Visual Studio Code yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="0110e-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="0110e-116">Daha fazla bilgi için [ C# Visual Studio Code uzantısı belgelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0110e-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="0110e-117">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="0110e-117">Get started</span></span>

<span data-ttu-id="0110e-118">Bu öğreticide, üç proje oluşturursunuz: bir kitaplık projesi, bu kitaplık projesi için testler ve kitaplığı kullanan bir konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="0110e-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="0110e-119">Bu konunun kaynağını GitHub 'daki DotNet/Samples deposunda [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) .</span><span class="sxs-lookup"><span data-stu-id="0110e-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="0110e-120">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="0110e-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="0110e-121">Visual Studio Code başlatın.</span><span class="sxs-lookup"><span data-stu-id="0110e-121">Start Visual Studio Code.</span></span> <span data-ttu-id="0110e-122">Visual Studio Code ' de gömülü bir terminal açmak için <kbd>CTRL</kbd> + <kbd>\`</kbd> tuşuna basın (backquote veya backtick karakteri) veya menüden **> tümleşik Terminal görüntüle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="0110e-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="0110e-123">Visual Studio Code dışında çalışmayı tercih ediyorsanız, bir dış kabuğu Explorer **komut istemi** komutunda aç (Mac veya Linux 'ta**terminalde aç** ) ile açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0110e-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="0110e-124">Bir veya daha fazla .NET Core projesi için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="0110e-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="0110e-125">Terminalde, *altın*adlı yeni [`dotnet new`](../tools/dotnet-new.md) bir klasör içinde *altın. sln* yeni bir çözüm oluşturmak için komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0110e-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```console
dotnet new sln -o golden
```

<span data-ttu-id="0110e-126">New *altın* klasörüne gidin ve Kitaplık klasöründe,*Library. csproj* ve *Class1.cs*olmak üzere iki dosya üreten *bir kitaplık projesi* oluşturmak için aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="0110e-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="0110e-127">Yeni oluşturulan *Library. csproj* projesini çözüme eklemek için [komutunuyürütün:`dotnet sln`](../tools/dotnet-sln.md)</span><span class="sxs-lookup"><span data-stu-id="0110e-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="0110e-128">*Library. csproj* dosyası aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="0110e-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="0110e-129">Kitaplık yöntemlerimiz JSON biçimindeki nesneleri serileştirmek ve serisini kaldıramıyor.</span><span class="sxs-lookup"><span data-stu-id="0110e-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="0110e-130">JSON serileştirme ve serisini kaldırma desteklemek için `Newtonsoft.Json` NuGet paketine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0110e-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="0110e-131">Komut `dotnet add` , projeye yeni öğeler ekler.</span><span class="sxs-lookup"><span data-stu-id="0110e-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="0110e-132">Bir NuGet paketine başvuru eklemek için [`dotnet add package`](../tools/dotnet-add-package.md) komutunu kullanın ve paketin adını belirtin:</span><span class="sxs-lookup"><span data-stu-id="0110e-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="0110e-133">Bu, `Newtonsoft.Json` ve bağımlılıklarını kitaplık projesine ekler.</span><span class="sxs-lookup"><span data-stu-id="0110e-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="0110e-134">Alternatif olarak, *Library. csproj* dosyasını el ile düzenleyin ve aşağıdaki düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0110e-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="0110e-135">[](#dotnet-restore-note) Bağımlılıkları geri yükleyen (bkz. Note) ve bir Project. varlıklar. JSON dosyası dahil olmak üzere, içinde üç dosya içeren kitaplık içinde bir obj klasörü oluşturur: [`dotnet restore`](../tools/dotnet-restore.md)</span><span class="sxs-lookup"><span data-stu-id="0110e-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="0110e-136">*Kitaplık* klasöründe, *Class1.cs* dosyasını *Thing.cs*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="0110e-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="0110e-137">Kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0110e-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="0110e-138">Sınıfı, iki sayının toplamını döndüren, `Get`ancak toplamı bir dizeye dönüştürerek ve sonra bir tamsayıya seri durumdan çıkarmak için bir genel yöntem içerir. `Thing`</span><span class="sxs-lookup"><span data-stu-id="0110e-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="0110e-139">Bu, C# [ `using static` yönergeler](../../csharp/language-reference/keywords/using-static.md), [ifade-Bodied Üyeler](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)ve [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md)gibi birçok modern özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="0110e-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="0110e-140">[`dotnet build`](../tools/dotnet-build.md) Komutuyla kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0110e-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="0110e-141">Bu, *altın/Library/bin/Debug/Netstandard 1.4*altında bir *Library. dll* dosyası üretir:</span><span class="sxs-lookup"><span data-stu-id="0110e-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="0110e-142">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0110e-142">Create the test project</span></span>

<span data-ttu-id="0110e-143">Kitaplık için bir test projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0110e-143">Build a test project for the library.</span></span> <span data-ttu-id="0110e-144">*Altın* klasörden yeni bir test projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0110e-144">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="0110e-145">Çözüme test projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0110e-145">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="0110e-146">Önceki bölümde oluşturduğunuz kitaplığa bir proje başvurusu ekleyerek derleyicinin kitaplık projesini bulup kullanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0110e-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="0110e-147">[`dotnet add reference`](../tools/dotnet-add-reference.md) Şu komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0110e-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="0110e-148">Alternatif olarak, *Test-Library. csproj* dosyasını el ile düzenleyin ve aşağıdaki düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0110e-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="0110e-149">Bağımlılıklar düzgün şekilde yapılandırıldığına göre, kitaplığınız için testler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0110e-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="0110e-150">*UnitTest1.cs* açın ve içeriğini şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0110e-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="0110e-151">Birim testini (`Assert.NotEqual`) ilk oluşturduğunuzda 42 değerini 19 + 23 (veya 42) olarak, başarısız olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0110e-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="0110e-152">Birim testlerini oluştururken önemli bir adım testi, öncelikle mantığını onaylamak için bir kez başarısız olacak şekilde oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0110e-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="0110e-153">*Altın* klasöründen aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="0110e-153">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="0110e-154">Bu komutlar, bağımlılıkları geri yüklemek, onları derlemek ve testleri çalıştırmak için xUnit Test Çalıştırıcısı 'nı etkinleştirmek için tüm projeleri yinelemeli olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="0110e-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="0110e-155">Beklenen şekilde tek test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0110e-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="0110e-156">*UnitTest1.cs* dosyasını düzenleyin ve onaylama `Assert.NotEqual` öğesini olarak `Assert.Equal`değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0110e-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="0110e-157">Bu saati geçen testi yeniden çalıştırmak için *altın* klasöründen aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="0110e-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="0110e-158">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="0110e-158">Create the console app</span></span>

<span data-ttu-id="0110e-159">Aşağıdaki adımlar üzerinden oluşturduğunuz konsol uygulaması, daha önce oluşturduğunuz kitaplık projesine bir bağımlılık alır ve çalıştırıldığında kitaplık yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0110e-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="0110e-160">Bu geliştirme modelini kullanarak birden çok proje için yeniden kullanılabilir kitaplıklar oluşturmayı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="0110e-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="0110e-161">*Altın* klasöründen yeni bir konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0110e-161">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="0110e-162">Konsol uygulaması projesini çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0110e-162">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="0110e-163">Şu `dotnet add reference` komutu çalıştırarak kitaplıkta bağımlılığı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0110e-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="0110e-164">Çözümdeki `dotnet restore` üç projenin bağımlılıklarını geri yüklemek için çalıştırın ([bkz. Note](#dotnet-restore-note)).</span><span class="sxs-lookup"><span data-stu-id="0110e-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="0110e-165">*Program.cs* açın ve `Main` yönteminin içeriğini aşağıdaki satırla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="0110e-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="0110e-166">Program.cs dosyasının `using` en üstüne iki yönergeler ekleyin:</span><span class="sxs-lookup"><span data-stu-id="0110e-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="0110e-167">Yürütülebilir dosyayı çalıştırmak `dotnet run` için aşağıdaki komutu yürütün; `-p` burada `dotnet run` , ana uygulamanın projesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0110e-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="0110e-168">Uygulama "Yanıt 42" dizesini üretir.</span><span class="sxs-lookup"><span data-stu-id="0110e-168">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="0110e-169">Uygulamada hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0110e-169">Debug the application</span></span>

<span data-ttu-id="0110e-170">`WriteLine` Yöntemindeki ifadede`Main` bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0110e-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="0110e-171">İmleç `WriteLine` çizginin üzerindeyken <kbd>F9</kbd> tuşuna basarak veya kesme noktasını ayarlamak istediğiniz satırdaki sol kenar boşluğunda fareyle tıklanarak bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="0110e-171">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="0110e-172">Kod satırının yanındaki kenar boşluğunda kırmızı bir daire görünür.</span><span class="sxs-lookup"><span data-stu-id="0110e-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="0110e-173">Kesme noktasına ulaşıldığında, kesme noktası çizgisi yürütülmeden *önce* kod yürütme durur.</span><span class="sxs-lookup"><span data-stu-id="0110e-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="0110e-174">Visual Studio Code araç çubuğunda hata ayıklama simgesini seçerek hata ayıklayıcı sekmesini açın, menü çubuğundan **> hata ayıklamayı görüntüle** ' yi seçin ya da <kbd>CTRL</kbd>+<kbd>+ SHIFT</kbd>+' klavye kısayolunu<kbd>kullanın:</kbd></span><span class="sxs-lookup"><span data-stu-id="0110e-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Visual Studio Code hata ayıklayıcı](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="0110e-176">Uygulamayı hata ayıklayıcı altında başlatmak için Yürüt düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="0110e-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="0110e-177">Uygulama yürütme işlemini başlatır ve kesme noktasında çalışır.</span><span class="sxs-lookup"><span data-stu-id="0110e-177">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="0110e-178">`Get` Yöntemine adımlayın ve doğru bağımsız değişkenleri geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0110e-178">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="0110e-179">Yanıtın 42 olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="0110e-179">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

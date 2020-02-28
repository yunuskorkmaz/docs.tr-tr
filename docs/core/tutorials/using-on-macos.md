---
title: "Öğretici: Visual Studio Code kullanarak macOS 'ta .NET Core çözümü oluşturma"
description: Bu belge, Visual Studio Code kullanarak bir .NET Core çözümü oluşturmak için adımlar ve iş akışı sağlar.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156601"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="c27d8-103">Öğretici: Visual Studio Code kullanarak macOS 'ta .NET Core çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c27d8-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="c27d8-104">Bu belge, macOS için .NET Core çözümü oluşturmaya yönelik adımları ve iş akışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c27d8-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="c27d8-105">Projeler, birim testleri oluşturma, hata ayıklama araçlarını kullanma ve [NuGet](https://www.nuget.org/)aracılığıyla üçüncü taraf kitaplıklarını birleştirme hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="c27d8-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="c27d8-106">Bu makale macOS üzerinde [Visual Studio Code](https://code.visualstudio.com) kullanır.</span><span class="sxs-lookup"><span data-stu-id="c27d8-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c27d8-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c27d8-107">Prerequisites</span></span>

<span data-ttu-id="c27d8-108">[.NET Core SDK](https://dotnet.microsoft.com/download)'i yükler.</span><span class="sxs-lookup"><span data-stu-id="c27d8-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="c27d8-109">.NET Core SDK .NET Core Framework ve çalışma zamanının en son sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="c27d8-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="c27d8-110">[Visual Studio Code](https://code.visualstudio.com)'i yükler.</span><span class="sxs-lookup"><span data-stu-id="c27d8-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="c27d8-111">Bu makalenin kursu sırasında, .NET Core geliştirme deneyimini geliştiren Visual Studio Code uzantıları da yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="c27d8-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="c27d8-112">Visual Studio Code açıp C# <kbd>FN</kbd>+<kbd>F1</kbd> tuşlarına basarak Visual Studio Code uzantısını yükleyip Visual Studio Code paleti açın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>Fn</kbd>+<kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="c27d8-113">Uzantı listesini görmek için **EXT Install** yazın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="c27d8-114">C# Uzantıyı seçin.</span><span class="sxs-lookup"><span data-stu-id="c27d8-114">Select the C# extension.</span></span> <span data-ttu-id="c27d8-115">Uzantıyı etkinleştirmek için Visual Studio Code yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="c27d8-116">Daha fazla bilgi için [ C# Visual Studio Code uzantısı belgelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="c27d8-117">başlarken</span><span class="sxs-lookup"><span data-stu-id="c27d8-117">Get started</span></span>

<span data-ttu-id="c27d8-118">Bu öğreticide, üç proje oluşturursunuz: bir kitaplık projesi, bu kitaplık projesi için testler ve kitaplığı kullanan bir konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="c27d8-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="c27d8-119">Bu makalenin kaynağını GitHub 'daki DotNet/Samples deposunda [görüntüleyebilir veya indirebilirsiniz](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) .</span><span class="sxs-lookup"><span data-stu-id="c27d8-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this article at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="c27d8-120">İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="c27d8-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="c27d8-121">Visual Studio Code başlatın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-121">Start Visual Studio Code.</span></span> <span data-ttu-id="c27d8-122">Visual Studio Code yerleşik bir terminal açmak için <kbd>Ctrl</kbd> <kbd>\`</kbd> (backquote veya backtick karakteri) ya da menüden > **Terminal** **görüntüle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="c27d8-122">Press <kbd>Ctrl</kbd><kbd>\`</kbd> (the backquote or backtick character) or select **View** > **Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="c27d8-123">Visual Studio Code dışında çalışmayı tercih ediyorsanız, bir dış kabuğu, **komut istemi** komutunda aç (MacOS veya Linux 'ta**terminalde aç** ) ile açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c27d8-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on macOS or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="c27d8-124">Bir veya daha fazla .NET Core projesi için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="c27d8-125">Terminalde, *altın*adlı yeni bir klasörde *altın. sln* yeni bir çözüm oluşturmak için [`dotnet new`](../tools/dotnet-new.md) komutunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="c27d8-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```dotnetcli
dotnet new sln -o golden
```

<span data-ttu-id="c27d8-126">New *altın* klasörüne gidin ve Kitaplık klasöründe,*Library. csproj* ve *Class1.cs*olmak üzere iki dosya üreten *bir kitaplık projesi* oluşturmak için aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="c27d8-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```dotnetcli
dotnet new classlib -o library
```

<span data-ttu-id="c27d8-127">Yeni oluşturulan *Library. csproj* projesini çözüme eklemek için [`dotnet sln`](../tools/dotnet-sln.md) komutunu yürütün:</span><span class="sxs-lookup"><span data-stu-id="c27d8-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```dotnetcli
dotnet sln add library/library.csproj
```

<span data-ttu-id="c27d8-128">*Library. csproj* dosyası aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c27d8-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="c27d8-129">Kitaplık yöntemlerimiz JSON biçimindeki nesneleri serileştirmek ve serisini kaldıramıyor.</span><span class="sxs-lookup"><span data-stu-id="c27d8-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="c27d8-130">JSON serileştirme ve serisini kaldırma desteği için `Newtonsoft.Json` NuGet paketine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c27d8-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="c27d8-131">`dotnet add` komutu bir projeye yeni öğeler ekler.</span><span class="sxs-lookup"><span data-stu-id="c27d8-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="c27d8-132">Bir NuGet paketine başvuru eklemek için, [`dotnet add package`](../tools/dotnet-add-package.md) komutunu kullanın ve paketin adını belirtin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```dotnetcli
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="c27d8-133">Bu, `Newtonsoft.Json` ve bağımlılıklarını kitaplık projesine ekler.</span><span class="sxs-lookup"><span data-stu-id="c27d8-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="c27d8-134">Alternatif olarak, *Library. csproj* dosyasını el ile düzenleyin ve aşağıdaki düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="c27d8-135">Bağımlılıkları geri yükleyen [`dotnet restore`](../tools/dotnet-restore.md)yürütün ([bkz. Note](#dotnet-restore-note)) ve içinde bir *Project. varlıklar. JSON* dosyası dahil olmak üzere üç dosya içeren *kitaplık* içinde bir *obj* klasörü oluşturur:</span><span class="sxs-lookup"><span data-stu-id="c27d8-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```dotnetcli
dotnet restore
```

<span data-ttu-id="c27d8-136">*Kitaplık* klasöründe, *Class1.cs* dosyasını *Thing.cs*olarak yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="c27d8-137">Kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="c27d8-138">`Thing` sınıfı, iki sayının toplamını döndüren ve sonra toplamı bir dizeye dönüştürerek ve sonra bir tamsayı olarak seri durumdan çıkarmak için bir genel yöntem içerir, `Get`.</span><span class="sxs-lookup"><span data-stu-id="c27d8-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="c27d8-139">C# Bu, [`using static` yönergeleri](../../csharp/language-reference/keywords/using-static.md), [ifade-Bodied Üyeler](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)ve [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md)gibi birçok modern özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="c27d8-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="c27d8-140">[`dotnet build`](../tools/dotnet-build.md) komutuyla kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c27d8-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="c27d8-141">Bu, *altın/Library/bin/Debug/Netstandard 1.4*altında bir *Library. dll* dosyası üretir:</span><span class="sxs-lookup"><span data-stu-id="c27d8-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="c27d8-142">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c27d8-142">Create the test project</span></span>

<span data-ttu-id="c27d8-143">Kitaplık için bir test projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c27d8-143">Build a test project for the library.</span></span> <span data-ttu-id="c27d8-144">*Altın* klasörden yeni bir test projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c27d8-144">From the *golden* folder, create a new test project:</span></span>

```dotnetcli
dotnet new xunit -o test-library
```

<span data-ttu-id="c27d8-145">Çözüme test projesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-145">Add the test project to the solution:</span></span>

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="c27d8-146">Önceki bölümde oluşturduğunuz kitaplığa bir proje başvurusu ekleyerek derleyicinin kitaplık projesini bulup kullanmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c27d8-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="c27d8-147">[`dotnet add reference`](../tools/dotnet-add-reference.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c27d8-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="c27d8-148">Alternatif olarak, *Test-Library. csproj* dosyasını el ile düzenleyin ve aşağıdaki düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="c27d8-149">Bağımlılıklar düzgün şekilde yapılandırıldığına göre, kitaplığınız için testler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c27d8-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="c27d8-150">*UnitTest1.cs* açın ve içeriğini şu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="c27d8-151">Birim testini (`Assert.NotEqual`) ilk oluşturduğunuzda 42 değerini 19 + 23 (veya 42) değerine eşit olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="c27d8-152">Birim testlerini oluştururken önemli bir adım testi, öncelikle mantığını onaylamak için bir kez başarısız olacak şekilde oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="c27d8-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="c27d8-153">*Altın* klasöründen aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="c27d8-153">From the *golden* folder, execute the following commands:</span></span>

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="c27d8-154">Bu komutlar, bağımlılıkları geri yüklemek, onları derlemek ve testleri çalıştırmak için xUnit Test Çalıştırıcısı 'nı etkinleştirmek için tüm projeleri yinelemeli olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="c27d8-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="c27d8-155">Beklenen şekilde tek test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c27d8-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="c27d8-156">*UnitTest1.cs* dosyasını düzenleyin ve onaylama `Assert.NotEqual` `Assert.Equal`olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c27d8-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="c27d8-157">Bu saati geçen testi yeniden çalıştırmak için *altın* klasöründen aşağıdaki komutu yürütün:</span><span class="sxs-lookup"><span data-stu-id="c27d8-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="c27d8-158">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="c27d8-158">Create the console app</span></span>

<span data-ttu-id="c27d8-159">Aşağıdaki adımlar üzerinden oluşturduğunuz konsol uygulaması, daha önce oluşturduğunuz kitaplık projesine bir bağımlılık alır ve çalıştırıldığında kitaplık yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="c27d8-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="c27d8-160">Bu geliştirme modelini kullanarak birden çok proje için yeniden kullanılabilir kitaplıklar oluşturmayı görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c27d8-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="c27d8-161">*Altın* klasöründen yeni bir konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c27d8-161">Create a new console application from the *golden* folder:</span></span>

```dotnetcli
dotnet new console -o app
```

<span data-ttu-id="c27d8-162">Konsol uygulaması projesini çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-162">Add the console app project to the solution:</span></span>

```dotnetcli
dotnet sln add app/app.csproj
```

<span data-ttu-id="c27d8-163">`dotnet add reference` komutunu çalıştırarak kitaplıkta bağımlılığı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="c27d8-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="c27d8-164">Çözümdeki üç projenin bağımlılıklarını geri yüklemek için `dotnet restore` ([bkz. Note](#dotnet-restore-note)) ' i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="c27d8-165">*Program.cs* ' i açın ve `Main` yönteminin içeriğini aşağıdaki satırla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="c27d8-166">*Program.cs* dosyasının en üstüne iki `using` yönergesi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c27d8-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="c27d8-167">Yürütülebilir dosyayı çalıştırmak için aşağıdaki `dotnet run` komutunu yürütün; burada, `dotnet run` `-p` seçeneği, ana uygulamanın projesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c27d8-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="c27d8-168">Uygulama "Yanıt 42" dizesini üretir.</span><span class="sxs-lookup"><span data-stu-id="c27d8-168">The app produces the string "The answer is 42".</span></span>

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="c27d8-169">Uygulamada hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c27d8-169">Debug the application</span></span>

<span data-ttu-id="c27d8-170">`Main` yönteminde `WriteLine` bildiriminde bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="c27d8-171">İmleç `WriteLine` çizginin üzerindeyken ya da kesme noktasını ayarlamak istediğiniz satırdaki sol kenar boşluğunda fareyle tıklanarak, <kbd>Fn</kbd>+<kbd>F9</kbd> tuşuna basarak bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-171">Do this by either pressing the <kbd>Fn</kbd>+<kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="c27d8-172">Kod satırının yanındaki kenar boşluğunda kırmızı bir daire görünür.</span><span class="sxs-lookup"><span data-stu-id="c27d8-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="c27d8-173">Kesme noktasına ulaşıldığında, kesme noktası çizgisi yürütülmeden *önce* kod yürütme durur.</span><span class="sxs-lookup"><span data-stu-id="c27d8-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="c27d8-174">Visual Studio Code araç çubuğunda hata ayıklama simgesini seçerek hata ayıklayıcı sekmesini açın, menü çubuğundan >  **hata ayıklamayı** görüntüle ' yi seçin veya <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>klavye kısayolunu kullanın</kbd>:</span><span class="sxs-lookup"><span data-stu-id="c27d8-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View** > **Debug** from the menu bar, or using the keyboard shortcut <kbd>&#8679;</kbd><kbd>&#8984;</kbd><kbd>D</kbd>:</span></span>

![Visual Studio Code hata ayıklayıcı](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="c27d8-176">Uygulamayı hata ayıklayıcı altında başlatmak için Yürüt düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="c27d8-177">Bu projede hem bir test projesi hem de bir uygulama oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="c27d8-177">You've created both a test project and an application in this project.</span></span> <span data-ttu-id="c27d8-178">Hata ayıklayıcı hangi projeyi başlatmak istediğinizi sorar.</span><span class="sxs-lookup"><span data-stu-id="c27d8-178">The debugger asks which project you want to start.</span></span> <span data-ttu-id="c27d8-179">"Uygulama" projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c27d8-179">Select the "app" project.</span></span> <span data-ttu-id="c27d8-180">Uygulama yürütme işlemini başlatır ve kesme noktasında çalışır.</span><span class="sxs-lookup"><span data-stu-id="c27d8-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="c27d8-181">`Get` yöntemine adımla ve doğru bağımsız değişkenleri geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c27d8-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="c27d8-182">Yanıtın 42 olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c27d8-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

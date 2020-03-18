---
title: "Öğretici: Visual Studio Code kullanarak macOS'ta bir .NET Core çözümü oluşturun"
description: Bu belge, Visual Studio Code kullanarak bir .NET Core Solution oluşturmak için adımlar ve iş akışı sağlar.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156601"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="01e50-103">Öğretici: Visual Studio Code kullanarak macOS'ta bir .NET Core çözümü oluşturun</span><span class="sxs-lookup"><span data-stu-id="01e50-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="01e50-104">Bu belge, macOS için bir .NET Core çözümü oluşturmak için adımları ve iş akışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="01e50-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="01e50-105">[NuGet](https://www.nuget.org/)aracılığıyla proje oluşturmayı, birim testleri yapmayı, hata ayıklama araçlarını nasıl kullanacağınızı ve üçüncü taraf kitaplıklarını nasıl birleştirerek nasıl kullanacağınızı öğrenin.</span><span class="sxs-lookup"><span data-stu-id="01e50-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="01e50-106">Bu makalede, macOS'ta [Visual Studio Kodu](https://code.visualstudio.com) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01e50-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="01e50-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="01e50-107">Prerequisites</span></span>

<span data-ttu-id="01e50-108">[.NET Çekirdek SDK'yı](https://dotnet.microsoft.com/download)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="01e50-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="01e50-109">.NET Core SDK, .NET Core çerçevesinin ve çalışma zamanının en son sürümüne yer verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01e50-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="01e50-110">[Visual Studio Kodunu](https://code.visualstudio.com)Yükleyin.</span><span class="sxs-lookup"><span data-stu-id="01e50-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="01e50-111">Bu makale nin seyri sırasında,.NET Core geliştirme deneyimini geliştiren Visual Studio Code uzantılarını da yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="01e50-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="01e50-112">Visual Studio Code Kodunu açarak ve Visual Studio Code paletini açmak için <kbd>Fn</kbd>+<kbd>F1</kbd> tuşuna basarak Visual Studio Code C# uzantısını yükleyin.</span><span class="sxs-lookup"><span data-stu-id="01e50-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>Fn</kbd>+<kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="01e50-113">Uzantıların listesini görmek için **ext yükleme** yazın.</span><span class="sxs-lookup"><span data-stu-id="01e50-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="01e50-114">C# uzantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="01e50-114">Select the C# extension.</span></span> <span data-ttu-id="01e50-115">Uzantıyı etkinleştirmek için Visual Studio Code'u yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="01e50-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="01e50-116">Daha fazla bilgi için [Visual Studio Code C# Extension belgelerine](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="01e50-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="01e50-117">Başlarken</span><span class="sxs-lookup"><span data-stu-id="01e50-117">Get started</span></span>

<span data-ttu-id="01e50-118">Bu öğreticide, üç proje oluşturursunuz: bir kitaplık projesi, kitaplık projesi için testler ve kitaplığı kullanan bir konsol uygulaması.</span><span class="sxs-lookup"><span data-stu-id="01e50-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="01e50-119">Bu [makalenin kaynağını](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) GitHub'daki dotnet/samples deposundan görüntüleyebilir veya indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01e50-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this article at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="01e50-120">İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.</span><span class="sxs-lookup"><span data-stu-id="01e50-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="01e50-121">Visual Studio Code'u başlatın.</span><span class="sxs-lookup"><span data-stu-id="01e50-121">Start Visual Studio Code.</span></span> <span data-ttu-id="01e50-122">Visual Studio Code'da gömülü bir terminal açmak için <kbd>Ctrl</kbd> <kbd>\`</kbd> 'ye (backquote veya backtick karakteri) basın veya menüden**Terminali** **Görüntüle'yi** > seçin.</span><span class="sxs-lookup"><span data-stu-id="01e50-122">Press <kbd>Ctrl</kbd><kbd>\`</kbd> (the backquote or backtick character) or select **View** > **Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="01e50-123">Visual Studio Code dışında çalışmayı tercih ederseniz Explorer **Open in Command Prompt** komutu (macOS veya**Linux'ta Terminal'de açık)** ile harici bir kabuk açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01e50-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on macOS or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="01e50-124">Bir veya daha fazla .NET Core projesi için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="01e50-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="01e50-125">Terminalde, golden [`dotnet new`](../tools/dotnet-new.md) adlı yeni bir klasör içinde yeni bir çözüm *golden* *golden.sln* oluşturmak için komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="01e50-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```dotnetcli
dotnet new sln -o golden
```

<span data-ttu-id="01e50-126">Kitaplık klasöründe*library.csproj* ve *Class1.cs*olmak üzere iki dosya üreten bir kitaplık projesi *library* oluşturmak için yeni *altın* klasöre gidin ve aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="01e50-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```dotnetcli
dotnet new classlib -o library
```

<span data-ttu-id="01e50-127">Yeni [`dotnet sln`](../tools/dotnet-sln.md) oluşturulan *library.csproj* projesini çözüme eklemek için komutu uygulayın:</span><span class="sxs-lookup"><span data-stu-id="01e50-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```dotnetcli
dotnet sln add library/library.csproj
```

<span data-ttu-id="01e50-128">*Library.csproj* dosyası aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="01e50-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="01e50-129">Kitaplık yöntemlerimiz json formatında nesneleri seri hale ve deserialize eder.</span><span class="sxs-lookup"><span data-stu-id="01e50-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="01e50-130">JSON serileştirme ve deserialization desteklemek için `Newtonsoft.Json` NuGet paketine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="01e50-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="01e50-131">Komut, `dotnet add` projeye yeni öğeler ekler.</span><span class="sxs-lookup"><span data-stu-id="01e50-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="01e50-132">NuGet paketine başvuru eklemek için [`dotnet add package`](../tools/dotnet-add-package.md) komutu kullanın ve paketin adını belirtin:</span><span class="sxs-lookup"><span data-stu-id="01e50-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```dotnetcli
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="01e50-133">Bu, `Newtonsoft.Json` kitaplık projesine bağımlılıkları ve bağımlılıklarını ekler.</span><span class="sxs-lookup"><span data-stu-id="01e50-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="01e50-134">Alternatif olarak, *library.csproj* dosyasını el ile edin ve aşağıdaki düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="01e50-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="01e50-135">Bağımlılıkları geri [`dotnet restore`](../tools/dotnet-restore.md)yükleyen ve içinde *project.assets.json* dosyası da dahil olmak üzere üç dosya içeren *kitaplık* içinde bir *obj* klasörü oluşturan Yürütme , ([bkz.](#dotnet-restore-note)</span><span class="sxs-lookup"><span data-stu-id="01e50-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```dotnetcli
dotnet restore
```

<span data-ttu-id="01e50-136">*Kitaplık* klasöründe, dosyayı *Class1.cs* *Thing.cs'* e yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="01e50-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="01e50-137">Kodu aşağıdakilerle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="01e50-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="01e50-138">Sınıf, `Thing` iki sayının `Get`toplamını döndüren, ancak toplamı bir dize dönüştürüp sonra bir tamsayıya dönüştürerek bunu yapan bir ortak yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="01e50-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="01e50-139">Bu, [ `using static` yönergeler,](../../csharp/language-reference/keywords/using-static.md) [ifade gövdeli üyeler](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)ve [dize enterpolasyonu](../../csharp/language-reference/tokens/interpolated.md)gibi bir dizi modern C# özelliğinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="01e50-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="01e50-140">[`dotnet build`](../tools/dotnet-build.md) Komutla kitaplığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="01e50-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="01e50-141">Bu *altın/kütüphane/bin/Debug/netstandard1.4*altında bir *library.dll* dosyası oluşturur:</span><span class="sxs-lookup"><span data-stu-id="01e50-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="01e50-142">Test projesini oluşturma</span><span class="sxs-lookup"><span data-stu-id="01e50-142">Create the test project</span></span>

<span data-ttu-id="01e50-143">Kitaplık için bir test projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="01e50-143">Build a test project for the library.</span></span> <span data-ttu-id="01e50-144">*Altın* klasörden yeni bir test projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="01e50-144">From the *golden* folder, create a new test project:</span></span>

```dotnetcli
dotnet new xunit -o test-library
```

<span data-ttu-id="01e50-145">Test projesini çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="01e50-145">Add the test project to the solution:</span></span>

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="01e50-146">Derleyicinin kitaplık projesini bulup kullanabilmesi için önceki bölümde oluşturduğunuz kitaplık bir proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="01e50-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="01e50-147">Komutu [`dotnet add reference`](../tools/dotnet-add-reference.md) kullanın:</span><span class="sxs-lookup"><span data-stu-id="01e50-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="01e50-148">Alternatif olarak, *test-library.csproj* dosyasını el ile edin ve aşağıdaki düğümü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="01e50-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="01e50-149">Bağımlılıklar düzgün şekilde yapılandırıldığına göre, kitaplığınız için testleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="01e50-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="01e50-150">*UnitTest1.cs* açın ve içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="01e50-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="01e50-151">42 değerinin 19+23 'e (veya 42)'ye eşit olmadığını, birim`Assert.NotEqual`testini ilk oluşturduğunuzda (veya 42) başarısız olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="01e50-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="01e50-152">Birim testleri oluşturmada önemli bir adım, testin mantığını doğrulamak için ilk önce başarısız olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="01e50-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="01e50-153">*Altın* klasörden aşağıdaki komutları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="01e50-153">From the *golden* folder, execute the following commands:</span></span>

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="01e50-154">Bu komutlar, bağımlılıkları geri yüklemek, bunları oluşturmak ve testleri çalıştırmak için xUnit test koşucusunu etkinleştirmek için tüm projeleri özyinelemeli olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="01e50-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="01e50-155">Beklediğiniz gibi, tek bir test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="01e50-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="01e50-156">*UnitTest1.cs* dosyasını edin ve `Assert.NotEqual` iddiayı ' dan ' a `Assert.Equal`değiştirin</span><span class="sxs-lookup"><span data-stu-id="01e50-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="01e50-157">Bu kez geçen testi yeniden çalıştırmak için *altın* klasörden aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="01e50-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="01e50-158">Konsol uygulamasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="01e50-158">Create the console app</span></span>

<span data-ttu-id="01e50-159">Aşağıdaki adımlar da oluşturduğunuz konsol uygulaması, daha önce oluşturduğunuz kitaplık projesine bağımlı hale getirir ve çalıştığında kitaplık yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="01e50-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="01e50-160">Bu geliştirme modelini kullanarak, birden çok proje için yeniden kullanılabilir kitaplıklar oluşturmanın nasıl olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="01e50-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="01e50-161">*Altın* klasörden yeni bir konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="01e50-161">Create a new console application from the *golden* folder:</span></span>

```dotnetcli
dotnet new console -o app
```

<span data-ttu-id="01e50-162">Konsol uygulaması projesini çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="01e50-162">Add the console app project to the solution:</span></span>

```dotnetcli
dotnet sln add app/app.csproj
```

<span data-ttu-id="01e50-163">`dotnet add reference` Komutu çalıştırarak kitaplığa bağımlılık oluşturun:</span><span class="sxs-lookup"><span data-stu-id="01e50-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="01e50-164">Çözümdeki üç projenin bağımlılıklarını geri yüklemek için çalıştırın `dotnet restore` ([bkz. nota bakınız).](#dotnet-restore-note)</span><span class="sxs-lookup"><span data-stu-id="01e50-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="01e50-165">*Program.cs* açın ve yöntemin `Main` içeriğini aşağıdaki satırla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="01e50-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="01e50-166">Program.cs `using` dosyasının üst bölümüne *Program.cs* iki yönerge ekleyin:</span><span class="sxs-lookup"><span data-stu-id="01e50-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="01e50-167">Ana uygulama `dotnet run` için projeyi `-p` belirtebilme `dotnet run` seçeneğinin bulunduğu, yürütülebilir'i çalıştırmak için aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="01e50-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="01e50-168">Uygulama "Yanıt 42"dir dizesini üretir.</span><span class="sxs-lookup"><span data-stu-id="01e50-168">The app produces the string "The answer is 42".</span></span>

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="01e50-169">Uygulamada hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="01e50-169">Debug the application</span></span>

<span data-ttu-id="01e50-170">`Main` Yöntemdeki deyimde `WriteLine` bir kesme noktası ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="01e50-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="01e50-171">İmleç `WriteLine` çizginin üzerindeyken <kbd>Fn</kbd>+<kbd>F9</kbd> tuşuna basarak veya kesme noktasını ayarlamak istediğiniz çizginin sol kenar boşluğundaki fareyi tıklatarak bunu yapın.</span><span class="sxs-lookup"><span data-stu-id="01e50-171">Do this by either pressing the <kbd>Fn</kbd>+<kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="01e50-172">Kod satırının yanındaki kenar boşluğunda kırmızı bir daire görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="01e50-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="01e50-173">Kesme noktasına ulaşıldığında, kesme noktası satırı yürütülmeden *önce* kod yürütme durdurulur.</span><span class="sxs-lookup"><span data-stu-id="01e50-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="01e50-174">Visual Studio Code araç çubuğundaki Hata Ayıklama simgesini seçerek, menü çubuğundan**Hata Ayıklama'yı** **Görüntüle'yi** > seçerek veya klavye kısayolu <kbd>&#8679;</kbd> <kbd>D</kbd> <kbd>&#8984;</kbd>kullanarak hata ayıklama sekmesini açın:</span><span class="sxs-lookup"><span data-stu-id="01e50-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View** > **Debug** from the menu bar, or using the keyboard shortcut <kbd>&#8679;</kbd><kbd>&#8984;</kbd><kbd>D</kbd>:</span></span>

![Görsel Stüdyo Kodu Debugger](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="01e50-176">Hata ayıklamanın altındaki uygulamayı başlatmak için Oynat düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="01e50-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="01e50-177">Bu projede hem bir test projesi hem de bir uygulama oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="01e50-177">You've created both a test project and an application in this project.</span></span> <span data-ttu-id="01e50-178">Hata ayıklayan hangi projeyi başlatmak istediğinizi sorar.</span><span class="sxs-lookup"><span data-stu-id="01e50-178">The debugger asks which project you want to start.</span></span> <span data-ttu-id="01e50-179">"Uygulama" projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="01e50-179">Select the "app" project.</span></span> <span data-ttu-id="01e50-180">Uygulama yürütmeye başlar ve kesme noktasına kadar çalışır ve burada durur.</span><span class="sxs-lookup"><span data-stu-id="01e50-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="01e50-181">Yönteme `Get` adım atın ve doğru bağımsız değişkenleri geçtiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="01e50-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="01e50-182">Cevabın 42 olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="01e50-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

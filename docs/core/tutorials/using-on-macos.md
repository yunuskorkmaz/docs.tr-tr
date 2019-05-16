---
title: MacOS üzerinde .NET Core ile çalışmaya başlama
description: Bu belge, Visual Studio Code'u kullanarak bir .NET Core çözümü oluşturmak için iş akışı ve adımları sağlar.
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: e79f5dd90124d2a1902194af2edbde0f5df107c7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633987"
---
# <a name="get-started-with-net-core-on-macos"></a><span data-ttu-id="9f92f-103">MacOS üzerinde .NET Core ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="9f92f-103">Get started with .NET Core on macOS</span></span>

<span data-ttu-id="9f92f-104">Bu belge, macOS için .NET Core çözüm oluşturmak için iş akışı ve adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f92f-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="9f92f-105">Projeleri, birim testleri oluşturma, hata ayıklama araçlarını kullanın ve aracılığıyla üçüncü taraf kitaplıklarını birleştirebilir öğrenin [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="9f92f-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="9f92f-106">Bu makalede [Visual Studio Code](https://code.visualstudio.com) macOS üzerinde.</span><span class="sxs-lookup"><span data-stu-id="9f92f-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f92f-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9f92f-107">Prerequisites</span></span>

<span data-ttu-id="9f92f-108">Yükleme [.NET Core SDK'sı](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="9f92f-108">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="9f92f-109">.NET Core SDK'sı, çalışma zamanı ve .NET Core framework en son sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="9f92f-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="9f92f-110">Yükleme [Visual Studio Code'u](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="9f92f-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="9f92f-111">Bu makalede Kurs sırasında Visual Studio Code, .NET Core geliştirme artıran uzantıları deneyimi de yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9f92f-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="9f92f-112">Visual Studio kodu açma ve basarak Visual Studio kodu C# uzantısı yükleme <kbd>F1</kbd> Visual Studio Code paletini açın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="9f92f-113">Tür **ext yükleme** uzantılarının listesini görmek için.</span><span class="sxs-lookup"><span data-stu-id="9f92f-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="9f92f-114">C# uzantısı'nı seçin.</span><span class="sxs-lookup"><span data-stu-id="9f92f-114">Select the C# extension.</span></span> <span data-ttu-id="9f92f-115">Uzantıyı etkinleştirmek için Visual Studio Code'u yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="9f92f-116">Daha fazla bilgi için [Visual Studio Code C# uzantısı belgeleri](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="9f92f-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="9f92f-117">Kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="9f92f-117">Get started</span></span>

<span data-ttu-id="9f92f-118">Bu öğreticide, üç proje oluştur: bir kitaplığı projesini test Bu kitaplık projesi ve bir konsol uygulaması yapar kitaplığını kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="9f92f-119">Yapabilecekleriniz [görüntüleme veya indirme kaynağını](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) dotnet/samples deposunda github'da Bu konu.</span><span class="sxs-lookup"><span data-stu-id="9f92f-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="9f92f-120">Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9f92f-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="9f92f-121">Visual Studio Code'u başlatın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-121">Start Visual Studio Code.</span></span> <span data-ttu-id="9f92f-122">Tuşuna <kbd>Ctrl</kbd> + <kbd> \` </kbd> (vurgulamasını belirtir ya da ters tırnak karakteri) veya **Görüntüle > tümleşik Terminalini** katıştırılmış açmak için menüden Visual Studio code'da Terminal.</span><span class="sxs-lookup"><span data-stu-id="9f92f-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="9f92f-123">Dış bir kabuk ile Gezgini'nde hala açabilirsiniz **komut istemi açın** komut (**terminalde açın** Mac veya Linux), Visual Studio Code dışında çalışmayı tercih ederseniz.</span><span class="sxs-lookup"><span data-stu-id="9f92f-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="9f92f-124">Bir veya daha fazla .NET Core projeleri için kapsayıcı görevi gören bir çözüm dosyası oluşturarak başlayın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="9f92f-125">Terminalde, oluşturun bir *altın* klasörü ve klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-125">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="9f92f-126">Bu klasör çözümünüzü köküdür.</span><span class="sxs-lookup"><span data-stu-id="9f92f-126">This folder is the root of your solution.</span></span> <span data-ttu-id="9f92f-127">Çalıştırma [ `dotnet new` ](../tools/dotnet-new.md) yeni bir çözüm oluşturmak için komut *golden.sln*:</span><span class="sxs-lookup"><span data-stu-id="9f92f-127">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="9f92f-128">Gelen *altın* klasörü, iki dosya oluşturur, bir kitaplık projesi oluşturmak için aşağıdaki komutu yürütün*library.csproj* ve *Class1.cs*, içinde*Kitaplığı* klasörü:</span><span class="sxs-lookup"><span data-stu-id="9f92f-128">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="9f92f-129">Yürütme [ `dotnet sln` ](../tools/dotnet-sln.md) yeni oluşturulan eklenecek komut *library.csproj* çözüme:</span><span class="sxs-lookup"><span data-stu-id="9f92f-129">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="9f92f-130">*Library.csproj* dosyası, aşağıdaki bilgileri içerir:</span><span class="sxs-lookup"><span data-stu-id="9f92f-130">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="9f92f-131">Bizim kitaplığı yöntemleri seri hale getrime ve JSON biçimindeki nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9f92f-131">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="9f92f-132">JSON seri hale getirme ve seri durumundan çıkarma desteklemek için bir başvuru ekleyin. `Newtonsoft.Json` NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="9f92f-132">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="9f92f-133">`dotnet add` Komutu, bir projeye yeni öğeler ekler.</span><span class="sxs-lookup"><span data-stu-id="9f92f-133">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="9f92f-134">Bir NuGet paketine başvuru eklemek için [ `dotnet add package` ](../tools/dotnet-add-package.md) komut ve paketinin adını belirtin:</span><span class="sxs-lookup"><span data-stu-id="9f92f-134">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="9f92f-135">Bu ekler `Newtonsoft.Json` ve bağımlılıklarını kitaplığı projesi.</span><span class="sxs-lookup"><span data-stu-id="9f92f-135">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="9f92f-136">Alternatif olarak, el ile düzenleyebilirsiniz *library.csproj* dosyasını açıp aşağıdaki düğüm ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9f92f-136">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="9f92f-137">Yürütme [ `dotnet restore` ](../tools/dotnet-restore.md), ([bkz. Not](#dotnet-restore-note)) bağımlılıkları yükler ve oluşturur bir *obj* klasörün içine *Kitaplığı* üç içindeki dosyaların dahil olmak üzere bir *project.assets.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="9f92f-137">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="9f92f-138">İçinde *Kitaplığı* klasör, dosya yeniden adlandırma *Class1.cs* için *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="9f92f-138">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="9f92f-139">Kodu aşağıdakiyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9f92f-139">Replace the code with the following:</span></span>

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

<span data-ttu-id="9f92f-140">`Thing` Sınıfı içeren bir genel yöntem `Get`, iki toplamı sayı ancak toplamı bir dizeye dönüştürmek ve sonra da bir tamsayıya seri durumdan çıkarılırken yazılabilmesine döndürür.</span><span class="sxs-lookup"><span data-stu-id="9f92f-140">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="9f92f-141">Bu kullanır modern C# özellikleri, bir dizi gibi [ `using static` yönergeleri](../../csharp/language-reference/keywords/using-static.md), [ifade gövdeli üyeler](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), ve [dize ilişkilendirme](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="9f92f-141">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="9f92f-142">Kitaplığı ile derleme [ `dotnet build` ](../tools/dotnet-build.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="9f92f-142">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="9f92f-143">Bu üreten bir *library.dll* altında dosya *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="9f92f-143">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="9f92f-144">Test projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f92f-144">Create the test project</span></span>

<span data-ttu-id="9f92f-145">Kitaplık için bir test projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f92f-145">Build a test project for the library.</span></span> <span data-ttu-id="9f92f-146">Gelen *altın* klasöründe yeni bir test projesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9f92f-146">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="9f92f-147">Test projesi çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9f92f-147">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="9f92f-148">Derleyici, bulma ve kitaplık projesi kullanın önceki bölümde oluşturduğunuz kitaplık proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9f92f-148">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="9f92f-149">Kullanım [ `dotnet add reference` ](../tools/dotnet-add-reference.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="9f92f-149">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="9f92f-150">Alternatif olarak, el ile düzenleyebilirsiniz *test library.csproj* dosyasını açıp aşağıdaki düğüm ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9f92f-150">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="9f92f-151">Bağımlılıkları doğru şekilde yapılandırdığınızdan, yönelik testler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f92f-151">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="9f92f-152">Açık *UnitTest1.cs* ve içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="9f92f-152">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="9f92f-153">' % S'değeri 42 19 + 23'ın (veya 42) eşit değil assert unutmayın ilk oluşturduğunuzda, birim testi (`Assert.NotEqual`), hangi başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9f92f-153">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="9f92f-154">Birim testleri oluşturmanın önemli bir adım mantığını onaylamak ilk kez başarısız test oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="9f92f-154">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="9f92f-155">Gelen *altın* klasöründe aşağıdaki komutları yürütün:</span><span class="sxs-lookup"><span data-stu-id="9f92f-155">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="9f92f-156">Bu komutlar bağımlılıklarını geri yükleme, bunları derlemek ve xUnit etkinleştirmek için tüm projeleri test Çalıştırıcısı testleri çalıştırmak için özyinelemeli bulma olur.</span><span class="sxs-lookup"><span data-stu-id="9f92f-156">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="9f92f-157">Beklediğiniz gibi tek bir test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="9f92f-157">The single test fails, as you expect.</span></span>

<span data-ttu-id="9f92f-158">Düzen *UnitTest1.cs* dosya ve onaylama gelen değiştirme `Assert.NotEqual` için `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="9f92f-158">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="9f92f-159">Aşağıdaki komutu yürütün *altın* bu süre geçtikten testi yeniden çalıştırmak için klasör:</span><span class="sxs-lookup"><span data-stu-id="9f92f-159">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="9f92f-160">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="9f92f-160">Create the console app</span></span>

<span data-ttu-id="9f92f-161">Aşağıdaki deyime oluşturduğunuz konsol uygulaması daha önce oluşturduğunuz ve yürütüldüğünde, kitaplık yöntemini çağırır. kitaplık projesi üzerinde bir bağımlılık alır.</span><span class="sxs-lookup"><span data-stu-id="9f92f-161">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="9f92f-162">Bu geliştirme desenini kullanarak, birden çok proje için yeniden kullanılabilir kitaplıklar oluşturma bakın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-162">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="9f92f-163">Yeni bir konsol uygulamasından oluşturma *altın* klasörü:</span><span class="sxs-lookup"><span data-stu-id="9f92f-163">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="9f92f-164">Konsol uygulaması projesi çözüme ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9f92f-164">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="9f92f-165">Bağımlılık çalıştırarak kitaplık oluşturma `dotnet add reference` komutu:</span><span class="sxs-lookup"><span data-stu-id="9f92f-165">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="9f92f-166">Çalıştırma `dotnet restore` ([bkz. Not](#dotnet-restore-note)) üç projeyi de çözümde bağımlılıklarını geri yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="9f92f-166">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="9f92f-167">Açık *Program.cs* ve içeriklerini `Main` yöntemine aşağıdaki satırı ile:</span><span class="sxs-lookup"><span data-stu-id="9f92f-167">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="9f92f-168">İki ekleme `using` yönergeleri üstüne *Program.cs* dosyası:</span><span class="sxs-lookup"><span data-stu-id="9f92f-168">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="9f92f-169">Aşağıdakileri yürütün `dotnet run` yürütülebilir, nerede çalıştırmak için komutu `-p` seçeneğini `dotnet run` ana uygulama için proje belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f92f-169">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="9f92f-170">Uygulama, "42 yanıttır" dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f92f-170">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="9f92f-171">Uygulamada hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9f92f-171">Debug the application</span></span>

<span data-ttu-id="9f92f-172">Bir kesme noktasında ayarlamak `WriteLine` deyiminde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9f92f-172">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="9f92f-173">Her iki basarak bunu <kbd>F9</kbd> tuşu imleci bittiğinde `WriteLine` fareyi kesme noktası ayarlamak istediğiniz satırda sol kenar boşluğunda tıklayabilir veya satır.</span><span class="sxs-lookup"><span data-stu-id="9f92f-173">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="9f92f-174">Kenar kod satırının yanında kırmızı bir daire görünür.</span><span class="sxs-lookup"><span data-stu-id="9f92f-174">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="9f92f-175">Kesme noktasına ulaşıldığında, yürütmeyi durdurur *önce* kesme noktası satırını yürütülür.</span><span class="sxs-lookup"><span data-stu-id="9f92f-175">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="9f92f-176">Visual Studio Code araç çubuğunda, hata ayıklama simgesini seçerek hata ayıklayıcı sekmesini açın seçerek **Görüntüle > hata ayıklama** menü çubuğu veya klavye kısayolunu kullanarak <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="9f92f-176">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Visual Studio Code hata ayıklayıcısı](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="9f92f-178">Hata ayıklayıcısı altında uygulamayı başlatmak için YÜRÜT düğmesine basın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-178">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="9f92f-179">Uygulamayı yürütmeyi başlatır ve burada durdurur kesme noktasına çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9f92f-179">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="9f92f-180">Adımlama `Get` yöntemi ve doğru bağımsız değişken geçirilen emin olun.</span><span class="sxs-lookup"><span data-stu-id="9f92f-180">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="9f92f-181">Yanıt 42 olduğunu doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="9f92f-181">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

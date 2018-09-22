---
title: .NET core CLI araçları ile uygulama dağıtımı
description: .NET Core uygulama dağıtımı ile komut satırı arabirimi (CLI) araçlarını edinin
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
ms.openlocfilehash: a7e810372d831699eae777186385e45fe65cdf45
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577613"
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="9e01a-103">Komut satırı arabirimi (CLI) araçları ile .NET Core uygulaması dağıtma</span><span class="sxs-lookup"><span data-stu-id="9e01a-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="9e01a-104">Dağıtabileceğiniz bir .NET Core uygulaması ya da farklı bir *framework bağımlı dağıtım*, uygulama ikili dosyalarını içerir, ancak hedef sistem üzerinde veya olarak .NET Core varlığını bağımlı bir *müstakil Dağıtım*, hem uygulama hem de .NET Core ikili dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="9e01a-105">Genel bakış için bkz. [.NET Core uygulaması dağıtımını](index.md).</span><span class="sxs-lookup"><span data-stu-id="9e01a-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="9e01a-106">Aşağıdaki bölümlerde nasıl kullanabileceğinizi gösteren [.NET Core komut satırı arabirimi Araçları](../tools/index.md) dağıtımları aşağıdaki türleri oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="9e01a-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="9e01a-107">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="9e01a-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="9e01a-108">Framework bağımlı dağıtım üçüncü taraf bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="9e01a-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="9e01a-109">Kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="9e01a-109">Self-contained deployment</span></span>
- <span data-ttu-id="9e01a-110">Üçüncü taraf bağımlılıkları kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="9e01a-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="9e01a-111">Komut satırından çalışırken, bir program düzenleyiciyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e01a-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="9e01a-112">Program düzenleyiciniz ise [Visual Studio Code](https://code.visualstudio.com), Visual Studio Code ortamınız içinde komut konsolunda seçerek açabilirsiniz **görünümü** > **tümleşik Terminalini**.</span><span class="sxs-lookup"><span data-stu-id="9e01a-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="9e01a-113">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="9e01a-113">Framework-dependent deployment</span></span>

<span data-ttu-id="9e01a-114">Herhangi bir üçüncü taraf bağımlılıkları olan bir framework bağımlı dağıtımının oluşturmaya, sınamaya ve uygulama yayımlama yalnızca içerir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="9e01a-115">C# dilinde yazılmış basit bir örnek işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-115">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="9e01a-116">Proje dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e01a-116">Create a project directory.</span></span>

   <span data-ttu-id="9e01a-117">Projeniz için bir dizin oluşturun ve geçerli dizininizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="9e01a-118">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e01a-118">Create the project.</span></span>

   <span data-ttu-id="9e01a-119">Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) yeni bir C# konsol projesi oluşturmak için veya [dotnet yeni konsol - vb dil](../tools/dotnet-new.md) bu dizinde yeni bir Visual Basic konsol projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9e01a-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project or [dotnet new console -lang vb](../tools/dotnet-new.md) to create a new Visual Basic console project in that directory.</span></span>

1. <span data-ttu-id="9e01a-120">Uygulamanın kaynak kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-120">Add the application's source code.</span></span>

   <span data-ttu-id="9e01a-121">Açık *Program.cs* veya *Program.vb* Düzenleyicisi'nde dosya ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-121">Open the *Program.cs* or *Program.vb* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="9e01a-122">Kullanıcının metin girmesini ister ve kullanıcı tarafından girilen kelimeler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9e01a-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="9e01a-123">Normal ifade kullanan `\w+` giriş metnindeki sözcükleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="9e01a-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]

1. <span data-ttu-id="9e01a-124">Proje bağımlılıkları ve Araçları'nı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-124">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="9e01a-125">Çalıştırma [dotnet restore](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)), projede belirtilen bağımlılıkları geri yüklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="9e01a-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="9e01a-126">Uygulamanızı hata ayıklama yapısını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e01a-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="9e01a-127">Kullanım [dotnet derleme](../tools/dotnet-build.md) uygulamanızı oluşturmak üzere komut veya [çalıştırma dotnet](../tools/dotnet-run.md) derlemek ve çalıştırmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="9e01a-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="9e01a-128">Uygulamanızı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="9e01a-128">Deploy your app.</span></span>

   <span data-ttu-id="9e01a-129">Hata ayıklama ve test programı sonra aşağıdaki komutu kullanarak dağıtımı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9e01a-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp2.1 -c Release
      ```
   <span data-ttu-id="9e01a-130">Bu, bir yayın (bir hata ayıklama yerine) oluşturur, uygulama sürümü.</span><span class="sxs-lookup"><span data-stu-id="9e01a-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="9e01a-131">Ortaya çıkan dosyalar adlı bir dizinde yerleştirilir *yayımlama* projenizin alt dizininde olan *bin* dizin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-131">The resulting files are placed in a directory named *publish*      that's in a subdirectory of your project's *bin* directory.</span></span>

   <span data-ttu-id="9e01a-132">Uygulamanızın dosyaları ile birlikte uygulamanızı hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayımlama işlemi yayar.</span><span class="sxs-lookup"><span data-stu-id="9e01a-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="9e01a-133">Dosya, öncelikle bir özel durum hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="9e01a-134">İle uygulamanızın dosyalarını dağıtmak değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e01a-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="9e01a-135">Uygulamanızı yayın derlemesinin hatalarını ayıklamak istediğiniz olay, ancak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

   <span data-ttu-id="9e01a-136">İstediğiniz gibi uygulama dosyalarını kümesinin tamamını dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e01a-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="9e01a-137">Örneğin, bunları bir Zip dosyasına paketleyin, basit bir kullanın `copy` komutunu ya da bunları seçtiğiniz herhangi bir yükleme paketi ile birlikte dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e01a-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

1. <span data-ttu-id="9e01a-138">Uygulamanızı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="9e01a-138">Run your app</span></span>

   <span data-ttu-id="9e01a-139">Yüklendikten sonra kullanıcılar uygulamanızı kullanarak yürütebilirsiniz `dotnet` komut ve uygulama dosya adı gibi sağlama `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="9e01a-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

   <span data-ttu-id="9e01a-140">Uygulama ikili dosyalarını ek olarak, yükleyicinizi de paylaşılan framework yükleyici paket veya uygulama yüklemesinin bir parçası olarak bir önkoşul olarak için kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="9e01a-141">Paylaşılan framework yönetici/kök erişimi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="9e01a-142">Framework bağımlı dağıtım üçüncü taraf bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="9e01a-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="9e01a-143">Bir framework bağımlı dağıtımının bir veya daha fazla üçüncü taraf bağımlılıkları olan bu bağımlılıkların projeniz için kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="9e01a-144">Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:</span><span class="sxs-lookup"><span data-stu-id="9e01a-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="9e01a-145">Gerekli üçüncü taraf kitaplıklara başvurular eklemek `<ItemGroup>` bölümünü, *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="9e01a-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="9e01a-146">Aşağıdaki `<ItemGroup>` bölüm üzerinde bir bağımlılık içeriyor [Json.NET](http://www.newtonsoft.com/json) bir üçüncü taraf kitaplığı:</span><span class="sxs-lookup"><span data-stu-id="9e01a-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="9e01a-147">Henüz yapmadıysanız, üçüncü taraf bağımlılığı'nı içeren NuGet paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="9e01a-148">Paketi indirmek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu.</span><span class="sxs-lookup"><span data-stu-id="9e01a-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="9e01a-149">Bağımlılık yerel NuGet önbelleğini dışında çözümlendiğinden zaman yayımlama, sisteminizde kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="9e01a-150">Üçüncü taraf bağımlılıkları olan bir framework bağımlı dağıtım yalnızca üçüncü taraf bağımlılıklarını olarak taşınabilir olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9e01a-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="9e01a-151">Örneğin, bir üçüncü taraf kitaplığı yalnızca macOS destekliyorsa, uygulamayı Windows sistemleri için taşınabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="9e01a-152">Bu, üçüncü taraf bağımlılığı yerel kodu bağımlı olması durumunda gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="9e01a-153">Bunun iyi bir örnektir [Kestrel sunucu](/aspnet/core/fundamentals/servers/kestrel), üzerinde yerel bir bağımlılık gerektiren [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="9e01a-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="9e01a-154">Bu tür bir üçüncü taraf bağımlılığı bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktısını bir klasöre her biri için içeren [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) yerel bağımlılık destekleyen (ve kendi NuGet paketini var).</span><span class="sxs-lookup"><span data-stu-id="9e01a-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="9e01a-155">Üçüncü taraf bağımlılıkları olmadan kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="9e01a-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="9e01a-156">Üçüncü taraf bağımlılıkları içerir olmadan projesi oluşturarak kendi içinde bir dağıtım dağıtma değiştirme *csproj* oluşturmaya, sınamaya ve uygulama yayımlama dosyası.</span><span class="sxs-lookup"><span data-stu-id="9e01a-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="9e01a-157">C# dilinde yazılmış basit bir örnek işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="9e01a-158">Örneğin, kullanarak kendi içinde dağıtımı oluşturma işlemi gösterilmektedir [dotnet yardımcı programı](../tools/dotnet.md) komut satırından.</span><span class="sxs-lookup"><span data-stu-id="9e01a-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="9e01a-159">Proje için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e01a-159">Create a directory for the project.</span></span>

   <span data-ttu-id="9e01a-160">Projeniz için bir dizin oluşturun ve geçerli dizininizi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="9e01a-161">Projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e01a-161">Create the project.</span></span>

   <span data-ttu-id="9e01a-162">Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) bu dizinde yeni bir C# konsol projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="9e01a-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="9e01a-163">Uygulamanın kaynak kodunu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-163">Add the application's source code.</span></span>

   <span data-ttu-id="9e01a-164">Açık *Program.cs* Düzenleyicisi'nde dosya ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="9e01a-165">Kullanıcının metin girmesini ister ve kullanıcı tarafından girilen kelimeler görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9e01a-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="9e01a-166">Normal ifade kullanan `\w+` giriş metnindeki sözcükleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="9e01a-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](~/samples/snippets/core/deploying/cs/deployment-example.cs)]
   [!code-vb[deployment#1](~/samples/snippets/core/deploying/vb/deployment-example.vb)]
1. <span data-ttu-id="9e01a-167">Uygulamanızı hedefleyen platformlar tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="9e01a-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="9e01a-168">Oluşturma bir `<RuntimeIdentifiers>` içindeki `<PropertyGroup>` bölümünü, *csproj* uygulamanız hedefler ve hedeflediğiniz her platform için çalışma zamanı tanımlayıcı (RID) belirtin platformları tanımlayan dosya.</span><span class="sxs-lookup"><span data-stu-id="9e01a-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="9e01a-169">Aynı zamanda RID ayırmak için noktalı virgül eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9e01a-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="9e01a-170">Bkz: [çalışma zamanı tanımlayıcı Kataloğu](../rid-catalog.md) çalışma zamanı tanımlayıcılarının listesi.</span><span class="sxs-lookup"><span data-stu-id="9e01a-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="9e01a-171">Örneğin, aşağıdaki `<PropertyGroup>` bölümü gösterir uygulama 64-bit Windows 10 işletim sistemleri ve OS X sürüm 10.11 64-bit işletim sistemi üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="9e01a-172">Unutmayın `<RuntimeIdentifiers>` öğe görünebilir `<PropertyGroup>` içinde *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="9e01a-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="9e01a-173">Eksiksiz bir örnek *csproj* dosyası bu bölümde daha sonra görünür.</span><span class="sxs-lookup"><span data-stu-id="9e01a-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="9e01a-174">Proje bağımlılıkları ve Araçları'nı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="9e01a-175">Çalıştırma [dotnet restore](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)), projede belirtilen bağımlılıkları geri yüklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="9e01a-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="9e01a-176">Genelleştirme sabit modu kullanmak isteyip istemediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-176">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="9e01a-177">Uygulamanızı Linux hedefliyorsa, özellikle, avantajlarından yararlanarak dağıtımınızın toplam boyutunu azaltabilirsiniz [Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="9e01a-177">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).</span></span> <span data-ttu-id="9e01a-178">Genelleştirme sabit modu, genel olarak duyarlı değildir ve biçimlendirme kuralları, büyük/küçük harf kuralları ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için kullanışlıdır [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="9e01a-178">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="9e01a-179">Sabit modunu etkinleştirmek için projenize (çözümü değil) sağ **Çözüm Gezgini**seçip **Düzenle SCD.csproj** veya **Düzenle SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="9e01a-179">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="9e01a-180">Ardından aşağıdaki vurgulanan satırları dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9e01a-180">Then add the following highlighted lines to the file:</span></span>

 [!code-xml[globalization-invariant-mode](~/samples/snippets/core/deploying/xml/invariant.csproj)]

1. <span data-ttu-id="9e01a-181">Uygulamanızı hata ayıklama yapısını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e01a-181">Create a Debug build of your app.</span></span>

   <span data-ttu-id="9e01a-182">Komut satırından kullanma [dotnet derleme](../tools/dotnet-build.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="9e01a-182">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="9e01a-183">Hata ayıklama ve test programı sonra her platform için uygulamanızdan bu hedefler dağıtılacak dosyaların oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9e01a-183">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="9e01a-184">Kullanım `dotnet publish` her ikisi de şu şekilde platformlarını hedeflemek için komutu:</span><span class="sxs-lookup"><span data-stu-id="9e01a-184">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="9e01a-185">Bu, bir yayın (bir hata ayıklama yerine) oluşturur uygulamanızın her hedef platform sürümü.</span><span class="sxs-lookup"><span data-stu-id="9e01a-185">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="9e01a-186">Ortaya çıkan dosyalar adlı bir alt dizinine yerleştirilir *yayımlama* projenizin alt dizininde olan *.\bin\Release\netcoreapp2.1\<runtime_identifier >* alt.</span><span class="sxs-lookup"><span data-stu-id="9e01a-186">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp2.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="9e01a-187">Her alt uygulamanızı başlatmak için gerekli dosyaları (uygulama dosyalarınızı ve tüm .NET Core dosyaları) tam kümesini içerdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-187">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="9e01a-188">Uygulamanızın dosyaları ile birlikte uygulamanızı hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayımlama işlemi yayar.</span><span class="sxs-lookup"><span data-stu-id="9e01a-188">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="9e01a-189">Dosya, öncelikle bir özel durum hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-189">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="9e01a-190">Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e01a-190">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="9e01a-191">Uygulamanızı yayın derlemesinin hatalarını ayıklamak istediğiniz olay, ancak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-191">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="9e01a-192">Yayımlanan dosyaları istediğiniz herhangi bir şekilde dağıtın.</span><span class="sxs-lookup"><span data-stu-id="9e01a-192">Deploy the published files in any way you like.</span></span> <span data-ttu-id="9e01a-193">Örneğin, bunları bir Zip dosyasına paketleyin, basit bir kullanın `copy` komutunu ya da bunları seçtiğiniz herhangi bir yükleme paketi ile birlikte dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e01a-193">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="9e01a-194">Aşağıdaki tamamlandıktan *csproj* bu proje için dosya.</span><span class="sxs-lookup"><span data-stu-id="9e01a-194">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="9e01a-195">Üçüncü taraf bağımlılıkları kendi içinde dağıtım</span><span class="sxs-lookup"><span data-stu-id="9e01a-195">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="9e01a-196">Bir veya daha fazla üçüncü taraf bağımlılıkları kendi içinde bir dağıtımının bağımlılıkları ekleme içerir.</span><span class="sxs-lookup"><span data-stu-id="9e01a-196">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="9e01a-197">Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:</span><span class="sxs-lookup"><span data-stu-id="9e01a-197">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="9e01a-198">Herhangi bir üçüncü taraf kitaplıklara başvurular eklemek `<ItemGroup>` bölümünü, *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="9e01a-198">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="9e01a-199">Aşağıdaki `<ItemGroup>` bölümü, bir üçüncü taraf kitaplığı olarak Json.NET kullanır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-199">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="9e01a-200">Henüz yapmadıysanız, üçüncü taraf bağımlılığı sisteminize'nı içeren NuGet paketini indirin.</span><span class="sxs-lookup"><span data-stu-id="9e01a-200">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="9e01a-201">Bağımlılık uygulamanızı kullanılabilir hale getirmek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu.</span><span class="sxs-lookup"><span data-stu-id="9e01a-201">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="9e01a-202">Bağımlılık yerel NuGet önbelleğini dışında çözümlendiğinden zaman yayımlama, sisteminizde kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-202">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="9e01a-203">Aşağıdaki tamamlandıktan *csproj* bu proje için dosya:</span><span class="sxs-lookup"><span data-stu-id="9e01a-203">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="9e01a-204">Uygulamanızı dağıttığınızda, uygulamanızda kullanılan herhangi bir üçüncü taraf bağımlılıkları ile uygulama dosyalarınızı de yer alır.</span><span class="sxs-lookup"><span data-stu-id="9e01a-204">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="9e01a-205">Üçüncü taraf kitaplıklar, uygulama üzerinde çalıştığı sistemde gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9e01a-205">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="9e01a-206">Yalnızca bir üçüncü taraf kitaplığı ile kendi içinde bir dağıtım için bu kitaplığı tarafından desteklenen platformlar dağıtabileceğinizi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9e01a-206">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="9e01a-207">Bu yerel bağımlılıkları burada uygulamanın dağıtıldığı platform ile uyumlu olmalıdır framework bağımlı dağıtımında, üçüncü taraf bağımlılıklarının yerel bağımlılıkları olan olması için benzer.</span><span class="sxs-lookup"><span data-stu-id="9e01a-207">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

## <a name="see-also"></a><span data-ttu-id="9e01a-208">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e01a-208">See also</span></span>

* [<span data-ttu-id="9e01a-209">.NET core uygulama dağıtımı</span><span class="sxs-lookup"><span data-stu-id="9e01a-209">.NET Core Application Deployment</span></span>](index.md)
* [<span data-ttu-id="9e01a-210">.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="9e01a-210">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

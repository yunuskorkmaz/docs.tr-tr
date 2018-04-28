---
title: .NET core CLI araçları ile uygulama dağıtımı
description: .NET Core uygulama dağıtım araçları komut satırı arabirimi (CLI) ile bilgi edinin
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 21e824e6092b0d30e0499ff05c5471a291c8d269
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="12b23-103">Komut satırı arabirimi (CLI) araçları ile .NET Core uygulamaları dağıtma</span><span class="sxs-lookup"><span data-stu-id="12b23-103">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="12b23-104">.NET Core uygulama dağıtabilirsiniz ya da farklı bir *framework bağımlı dağıtım*, hangi uygulama ikili dosyaları içerir, ancak hedef sistemde veya olarak .NET Core varlığına bağlıdır bir *kendi içinde bulunan Dağıtım*, uygulamanız ve .NET Core ikili dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="12b23-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="12b23-105">Genel bir bakış için bkz: [.NET Core uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="12b23-105">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="12b23-106">Aşağıdaki bölümlerde nasıl kullanılacağını gösteren [.NET Core komut satırı arabirimi Araçları](../tools/index.md) dağıtımları şu tür oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="12b23-106">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="12b23-107">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="12b23-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="12b23-108">Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="12b23-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="12b23-109">Kendi içinde bulunan dağıtım</span><span class="sxs-lookup"><span data-stu-id="12b23-109">Self-contained deployment</span></span>
- <span data-ttu-id="12b23-110">Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım</span><span class="sxs-lookup"><span data-stu-id="12b23-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="12b23-111">Komut satırından çalışırken, bir program düzenleyiciyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12b23-111">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="12b23-112">Program düzenleyicinizi ise [Visual Studio Code](https://code.visualstudio.com), Visual Studio Code ortamınızın içinde bir komut konsolundan seçerek açabilirsiniz **Görünüm** > **tümleşik Terminal**.</span><span class="sxs-lookup"><span data-stu-id="12b23-112">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="12b23-113">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="12b23-113">Framework-dependent deployment</span></span>

<span data-ttu-id="12b23-114">Hiçbir üçüncü taraf bağımlılıkları framework bağımlı dağıtım dağıtma yalnızca derleme, test etme ve uygulama yayımlama içerir.</span><span class="sxs-lookup"><span data-stu-id="12b23-114">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="12b23-115">C# ile yazılmış basit bir örnek işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="12b23-115">A simple example written in C# illustrates the process.</span></span> 

1. <span data-ttu-id="12b23-116">Proje dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12b23-116">Create a project directory.</span></span>

   <span data-ttu-id="12b23-117">Projeniz için bir dizin oluşturun ve geçerli dizininiz yapın.</span><span class="sxs-lookup"><span data-stu-id="12b23-117">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="12b23-118">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12b23-118">Create the project.</span></span>

   <span data-ttu-id="12b23-119">Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) bu dizinde yeni bir C# konsol projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="12b23-119">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="12b23-120">Uygulamanın kaynak kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12b23-120">Add the application's source code.</span></span>

   <span data-ttu-id="12b23-121">Açık *Program.cs* dosya düzenleyicinizde ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="12b23-121">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="12b23-122">Metin girmesini ister ve kullanıcı tarafından girilen ayrı sözcükleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12b23-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="12b23-123">Normal ifade kullanan `\w+` giriş metni sözcükleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="12b23-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="12b23-124">Proje bağımlılıkları ve araçları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="12b23-124">Update the project's dependencies and tools.</span></span>
 
   <span data-ttu-id="12b23-125">Çalıştırma [dotnet geri yükleme](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)) projenizde belirtilen bağımlılıkları geri yüklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="12b23-125">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="12b23-126">Hata ayıklama derlemesi, uygulamanızın oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12b23-126">Create a Debug build of your app.</span></span>

   <span data-ttu-id="12b23-127">Kullanım [dotnet yapı](../tools/dotnet-build.md) Uygulamanızı yapılandırmak için komut veya [çalıştırmak dotnet](../tools/dotnet-run.md) oluşturmak ve çalıştırmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="12b23-127">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="12b23-128">Uygulamanızı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="12b23-128">Deploy your app.</span></span>

   <span data-ttu-id="12b23-129">Hata ayıklaması ve program test sonra aşağıdaki komutu kullanarak dağıtım oluşturun:</span><span class="sxs-lookup"><span data-stu-id="12b23-129">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   <span data-ttu-id="12b23-130">Bu sürüm (bir hata ayıklama yerine) oluşturur, uygulamanızın sürümü.</span><span class="sxs-lookup"><span data-stu-id="12b23-130">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="12b23-131">Ortaya çıkan dosyalar adlı bir dizinde yerleştirilir *yayımlama* projenizin bir alt dizin olan *bin* dizin.</span><span class="sxs-lookup"><span data-stu-id="12b23-131">The resulting files are placed in a directory named *publish* that's in a subdirectory of your project's *bin* directory.</span></span>

<span data-ttu-id="12b23-132">Uygulamanızın dosyaları yanı sıra, yayımlama işlemi uygulamanız ile ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="12b23-132">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="12b23-133">Dosya, öncelikle özel durumları hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="12b23-133">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="12b23-134">Uygulamanızın dosyalarıyla dağıtmak değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12b23-134">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="12b23-135">Uygulamanızın yayın derleme hatalarını ayıklamak istediğiniz olay, ancak kaydedin gerekir.</span><span class="sxs-lookup"><span data-stu-id="12b23-135">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="12b23-136">İstediğiniz şekilde uygulama dosyalarında tamamını dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12b23-136">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="12b23-137">Örneğin, bir ZIP dosyası paketini, basit bir kullanmak `copy` komutunu veya tercih ettiğiniz herhangi bir yükleme paketi ile dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12b23-137">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="12b23-138">Yüklendikten sonra kullanıcılar, uygulamanızın kullanarak yürütebilirsiniz `dotnet` komutu ve uygulama filename gibi sağlayarak `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="12b23-138">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="12b23-139">Uygulama ikili dosyaların yanı sıra, yükleyici de paylaşılan framework Yükleyici paketini ya da için uygulama yüklemesinin bir parçası olarak bir önkoşul olarak denetleyin.</span><span class="sxs-lookup"><span data-stu-id="12b23-139">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="12b23-140">Paylaşılan framework yüklemesi yönetici/kök erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="12b23-140">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="12b23-141">Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="12b23-141">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="12b23-142">Bir veya daha fazla üçüncü taraf bağımlılıkları framework bağımlı dağıtım dağıtma bu bağımlılıkların projeniz için kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="12b23-142">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="12b23-143">Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:</span><span class="sxs-lookup"><span data-stu-id="12b23-143">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="12b23-144">Gerekli üçüncü taraf kitaplıklarına başvurular ekleyin `<ItemGroup>` bölümü, *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="12b23-144">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="12b23-145">Aşağıdaki `<ItemGroup>` bölüm üzerinde bir bağımlılık içerir [Json.NET](http://www.newtonsoft.com/json) üçüncü taraf kitaplık olarak:</span><span class="sxs-lookup"><span data-stu-id="12b23-145">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="12b23-146">Henüz yapmadıysanız, üçüncü taraf bağımlılığı içeren NuGet paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="12b23-146">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="12b23-147">Paketini karşıdan yüklemek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu.</span><span class="sxs-lookup"><span data-stu-id="12b23-147">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="12b23-148">Bağımlılık yerel NuGet önbelleği dışında çözümlendiğinden zaman yayınlamak için sisteminizde kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="12b23-148">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="12b23-149">Üçüncü taraf bağımlılıkları framework bağımlı dağıtımla yalnızca üçüncü taraf bağımlılıkları olarak taşınabilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="12b23-149">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="12b23-150">Örneğin, bir üçüncü taraf kitaplık yalnızca macOS destekliyorsa, uygulamayı Windows sistemleri için taşınabilir değil.</span><span class="sxs-lookup"><span data-stu-id="12b23-150">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="12b23-151">Üçüncü taraf bağımlılığı yerel kodu bağımlı olması durumunda bu gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="12b23-151">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="12b23-152">Bu iyi bir örnektir [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), üzerindeki yerel bir bağımlılık gerektiren [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="12b23-152">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="12b23-153">Üçüncü taraf bağımlılığı bu tür bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktı bir klasör için her içerir [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) yerel bağımlılık destekleyen (ve onun NuGet paketi var).</span><span class="sxs-lookup"><span data-stu-id="12b23-153">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a> <span data-ttu-id="12b23-154">Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtımıdır</span><span class="sxs-lookup"><span data-stu-id="12b23-154">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="12b23-155">Üçüncü taraf bağımlılıkları içerir olmadan projesi oluşturma kendi içinde bulunan bir dağıtım dağıtma değiştirme *csproj* dosya oluşturma, test etme ve uygulama yayımlama.</span><span class="sxs-lookup"><span data-stu-id="12b23-155">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="12b23-156">C# ile yazılmış basit bir örnek işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="12b23-156">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="12b23-157">Örnek kullanarak kendi içinde bulunan dağıtımı oluşturmak nasıl gösterir [dotnet yardımcı programı](../tools/dotnet.md) komut satırından.</span><span class="sxs-lookup"><span data-stu-id="12b23-157">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="12b23-158">Proje için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12b23-158">Create a directory for the project.</span></span>

   <span data-ttu-id="12b23-159">Projeniz için bir dizin oluşturun ve geçerli dizininiz yapın.</span><span class="sxs-lookup"><span data-stu-id="12b23-159">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="12b23-160">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12b23-160">Create the project.</span></span>

   <span data-ttu-id="12b23-161">Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) bu dizinde yeni bir C# konsol projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="12b23-161">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="12b23-162">Uygulamanın kaynak kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12b23-162">Add the application's source code.</span></span>

   <span data-ttu-id="12b23-163">Açık *Program.cs* dosya düzenleyicinizde ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="12b23-163">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="12b23-164">Metin girmesini ister ve kullanıcı tarafından girilen ayrı sözcükleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12b23-164">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="12b23-165">Normal ifade kullanan `\w+` giriş metni sözcükleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="12b23-165">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="12b23-166">Uygulamanızı Hedef platformlar tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="12b23-166">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="12b23-167">Oluşturma bir `<RuntimeIdentifiers>` içinde etiketi `<PropertyGroup>` bölümü, *csproj* uygulamanızı hedefler ve hedeflediğiniz her platform için çalışma zamanı tanımlayıcı (RID) belirtin platformları tanımlayan dosyası.</span><span class="sxs-lookup"><span data-stu-id="12b23-167">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="12b23-168">Aynı zamanda RID ayırmak için noktalı virgül eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="12b23-168">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="12b23-169">Bkz: [çalışma zamanı tanımlayıcı katalog](../rid-catalog.md) çalışma zamanı tanımlayıcılarının listesi.</span><span class="sxs-lookup"><span data-stu-id="12b23-169">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span> 

   <span data-ttu-id="12b23-170">Örneğin, aşağıdaki `<PropertyGroup>` bölümü gösterir uygulama 64-bit Windows 10 işletim sistemleri ve 64-bit OS X sürüm 10.11 sürümünü işletim sisteminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="12b23-170">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="12b23-171">Unutmayın `<RuntimeIdentifiers>` öğesi içinde görünebilir `<PropertyGroup>` içinde *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="12b23-171">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="12b23-172">Tam bir örnek *csproj* dosyası bu bölümde daha sonra görünür.</span><span class="sxs-lookup"><span data-stu-id="12b23-172">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="12b23-173">Proje bağımlılıkları ve araçları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="12b23-173">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="12b23-174">Çalıştırma [dotnet geri yükleme](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)) projenizde belirtilen bağımlılıkları geri yüklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="12b23-174">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="12b23-175">Hata ayıklama derlemesi, uygulamanızın oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12b23-175">Create a Debug build of your app.</span></span>

   <span data-ttu-id="12b23-176">Komut satırından kullanma [dotnet yapı](../tools/dotnet-build.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="12b23-176">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="12b23-177">Hata ayıklaması ve program test sonra her platform için uygulamanız ile bu hedefler dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12b23-177">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="12b23-178">Kullanım `dotnet publish` her ikisi de aşağıdaki gibi platformları hedeflemesi için komut:</span><span class="sxs-lookup"><span data-stu-id="12b23-178">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="12b23-179">Bu sürüm (bir hata ayıklama yerine) oluşturur uygulamanız için her hedef platformu sürümü.</span><span class="sxs-lookup"><span data-stu-id="12b23-179">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="12b23-180">Ortaya çıkan dosyalar adlı bir alt dizinde yerleştirilir *yayımlama* projenizin bir alt dizin olan *.\bin\Release\netcoreapp1.1\<runtime_identifier >* alt dizin.</span><span class="sxs-lookup"><span data-stu-id="12b23-180">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp1.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="12b23-181">Her alt uygulamanızı başlatmak için gereken dosyaları (uygulama dosyalarınızı ve tüm .NET Core dosyaları) tam kümesi içerdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="12b23-181">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="12b23-182">Uygulamanızın dosyaları yanı sıra, yayımlama işlemi uygulamanız ile ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="12b23-182">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="12b23-183">Dosya, öncelikle özel durumları hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="12b23-183">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="12b23-184">Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12b23-184">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="12b23-185">Uygulamanızın yayın derleme hatalarını ayıklamak istediğiniz olay, ancak kaydedin gerekir.</span><span class="sxs-lookup"><span data-stu-id="12b23-185">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="12b23-186">İstediğiniz şekilde yayımlanan dosyalarında dağıtın.</span><span class="sxs-lookup"><span data-stu-id="12b23-186">Deploy the published files in any way you like.</span></span> <span data-ttu-id="12b23-187">Örneğin, bir ZIP dosyası paketini, basit bir kullanmak `copy` komutunu veya tercih ettiğiniz herhangi bir yükleme paketi ile dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12b23-187">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="12b23-188">Aşağıdaki tamamlandıktan *csproj* bu proje için dosya.</span><span class="sxs-lookup"><span data-stu-id="12b23-188">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="12b23-189">Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım</span><span class="sxs-lookup"><span data-stu-id="12b23-189">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="12b23-190">Bir veya daha fazla üçüncü taraf bağımlılıkları kendi içinde bulunan bir dağıtım dağıtma bağımlılıkları ekleme içerir.</span><span class="sxs-lookup"><span data-stu-id="12b23-190">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="12b23-191">Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:</span><span class="sxs-lookup"><span data-stu-id="12b23-191">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="12b23-192">Tüm üçüncü taraf kitaplıklarına başvurular ekleyin `<ItemGroup>` bölümü, *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="12b23-192">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="12b23-193">Aşağıdaki `<ItemGroup>` bölüm Json.NET üçüncü taraf kitaplık olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="12b23-193">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="12b23-194">Henüz yapmadıysanız, üçüncü taraf bağımlılığı sisteminize içeren NuGet paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="12b23-194">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="12b23-195">Bağımlılık uygulamanızı kullanılabilir hale getirmek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu.</span><span class="sxs-lookup"><span data-stu-id="12b23-195">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="12b23-196">Bağımlılık yerel NuGet önbelleği dışında çözümlendiğinden zaman yayınlamak için sisteminizde kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="12b23-196">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="12b23-197">Aşağıdaki tamamlandıktan *csproj* dosyası bu proje için:</span><span class="sxs-lookup"><span data-stu-id="12b23-197">The following is the complete *csproj* file for this project:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="12b23-198">Uygulamanızı dağıttığınızda, uygulamanızda kullanılan tüm üçüncü taraf bağımlılıkları ile uygulama dosyalarını da yer alır.</span><span class="sxs-lookup"><span data-stu-id="12b23-198">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="12b23-199">Üçüncü taraf kitaplıklar uygulama çalışırken sistemde gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="12b23-199">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="12b23-200">Yalnızca bir üçüncü taraf kitaplık müstakil dağıtımla bu kitaplığı tarafından desteklenen platformlar dağıtabileceğiniz olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="12b23-200">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="12b23-201">Bu burada yerel bağımlılıkları uygulamanın dağıtıldığı platform ile uyumlu olmalıdır framework bağımlı dağıtımında, üçüncü taraf bağımlılıkları yerel bağımlılıkları ile zorunda benzer.</span><span class="sxs-lookup"><span data-stu-id="12b23-201">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a><span data-ttu-id="12b23-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12b23-202">See also</span></span>

<span data-ttu-id="12b23-203">[.NET core uygulama dağıtımı](index.md) </span><span class="sxs-lookup"><span data-stu-id="12b23-203">[.NET Core Application Deployment](index.md) </span></span>  
[<span data-ttu-id="12b23-204">.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="12b23-204">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)   


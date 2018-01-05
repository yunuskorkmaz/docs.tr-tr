---
title: ".NET core CLI araçları ile uygulama dağıtımı"
description: ".NET Core uygulama dağıtım araçları komut satırı arabirimi (CLI) ile bilgi edinin"
keywords: ".NET, .NET core, .NET Core dağıtım"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 82ebe16d-5e1c-46cc-91e8-71974296429c
ms.workload: dotnetcore
ms.openlocfilehash: 302383ec44afd91d1df7f6c717b268d5f965c8c9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="deploying-net-core-apps-with-command-line-interface-cli-tools"></a><span data-ttu-id="1ed38-104">Komut satırı arabirimi (CLI) araçları ile .NET Core uygulamaları dağıtma</span><span class="sxs-lookup"><span data-stu-id="1ed38-104">Deploying .NET Core apps with command-line interface (CLI) tools</span></span>

<span data-ttu-id="1ed38-105">.NET Core uygulama dağıtabilirsiniz ya da farklı bir *framework bağımlı dağıtım*, hangi uygulama ikili dosyaları içerir, ancak hedef sistemde veya olarak .NET Core varlığına bağlıdır bir *kendi içinde bulunan Dağıtım*, uygulamanız ve .NET Core ikili dosyalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-105">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and the .NET Core binaries.</span></span> <span data-ttu-id="1ed38-106">Genel bir bakış için bkz: [.NET Core uygulama dağıtımı](index.md).</span><span class="sxs-lookup"><span data-stu-id="1ed38-106">For an overview, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="1ed38-107">Aşağıdaki bölümlerde nasıl kullanılacağını gösteren [.NET Core komut satırı arabirimi Araçları](../tools/index.md) dağıtımları şu tür oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="1ed38-107">The following sections show how to use [.NET Core command-line interface tools](../tools/index.md) to create the following kinds of deployments:</span></span>

- <span data-ttu-id="1ed38-108">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="1ed38-108">Framework-dependent deployment</span></span>
- <span data-ttu-id="1ed38-109">Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="1ed38-109">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="1ed38-110">Kendi içinde bulunan dağıtım</span><span class="sxs-lookup"><span data-stu-id="1ed38-110">Self-contained deployment</span></span>
- <span data-ttu-id="1ed38-111">Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım</span><span class="sxs-lookup"><span data-stu-id="1ed38-111">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="1ed38-112">Komut satırından çalışırken, bir program düzenleyiciyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ed38-112">When working from the command line, you can use a program editor of your choice.</span></span> <span data-ttu-id="1ed38-113">Program düzenleyicinizi ise [Visual Studio Code](https://code.visualstudio.com), Visual Studio Code ortamınızın içinde bir komut konsolundan seçerek açabilirsiniz **Görünüm** > **tümleşik Terminal**.</span><span class="sxs-lookup"><span data-stu-id="1ed38-113">If your program editor is [Visual Studio Code](https://code.visualstudio.com), you can open a command console inside your Visual Studio Code environment by selecting **View** > **Integrated Terminal**.</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="1ed38-114">Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="1ed38-114">Framework-dependent deployment</span></span>

<span data-ttu-id="1ed38-115">Hiçbir üçüncü taraf bağımlılıkları framework bağımlı dağıtım dağıtma yalnızca derleme, test etme ve uygulama yayımlama içerir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-115">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="1ed38-116">C# ile yazılmış basit bir örnek işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-116">A simple example written in C# illustrates the process.</span></span> 

1. <span data-ttu-id="1ed38-117">Proje dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ed38-117">Create a project directory.</span></span>

   <span data-ttu-id="1ed38-118">Projeniz için bir dizin oluşturun ve geçerli dizininiz yapın.</span><span class="sxs-lookup"><span data-stu-id="1ed38-118">Create a directory for your project and make it your current directory.</span></span>

1. <span data-ttu-id="1ed38-119">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ed38-119">Create the project.</span></span>

   <span data-ttu-id="1ed38-120">Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) bu dizinde yeni bir C# konsol projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1ed38-120">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="1ed38-121">Uygulamanın kaynak kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-121">Add the application's source code.</span></span>

   <span data-ttu-id="1ed38-122">Açık *Program.cs* dosya düzenleyicinizde ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-122">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="1ed38-123">Metin girmesini ister ve kullanıcı tarafından girilen ayrı sözcükleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ed38-123">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="1ed38-124">Normal ifade kullanan `\w+` giriş metni sözcükleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="1ed38-124">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="1ed38-125">Proje bağımlılıkları ve araçları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-125">Update the project's dependencies and tools.</span></span>
 
   <span data-ttu-id="1ed38-126">Çalıştırma [dotnet geri yükleme](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)) projenizde belirtilen bağımlılıkları geri yüklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="1ed38-126">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="1ed38-127">Hata ayıklama derlemesi, uygulamanızın oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ed38-127">Create a Debug build of your app.</span></span>

   <span data-ttu-id="1ed38-128">Kullanım [dotnet yapı](../tools/dotnet-build.md) Uygulamanızı yapılandırmak için komut veya [çalıştırmak dotnet](../tools/dotnet-run.md) oluşturmak ve çalıştırmak için komutu.</span><span class="sxs-lookup"><span data-stu-id="1ed38-128">Use the [dotnet build](../tools/dotnet-build.md) command to build your application or the [dotnet run](../tools/dotnet-run.md) command to build and run it.</span></span>

1. <span data-ttu-id="1ed38-129">Uygulamanızı dağıtın.</span><span class="sxs-lookup"><span data-stu-id="1ed38-129">Deploy your app.</span></span>

   <span data-ttu-id="1ed38-130">Hata ayıklaması ve program test sonra aşağıdaki komutu kullanarak dağıtım oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1ed38-130">After you've debugged and tested the program, create the deployment by using the following command:</span></span>

      ```console
      dotnet publish -f netcoreapp1.1 -c Release
      ```
   <span data-ttu-id="1ed38-131">Bu sürüm (bir hata ayıklama yerine) oluşturur, uygulamanızın sürümü.</span><span class="sxs-lookup"><span data-stu-id="1ed38-131">This creates a Release (rather than a Debug) version of your app.</span></span> <span data-ttu-id="1ed38-132">Ortaya çıkan dosyalar adlı bir dizinde yerleştirilir *yayımlama* projenizin bir alt dizin olan *bin* dizin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-132">The resulting files are placed in a directory named *publish* that's in a subdirectory of your project's *bin* directory.</span></span>

<span data-ttu-id="1ed38-133">Uygulamanızın dosyaları yanı sıra, yayımlama işlemi uygulamanız ile ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="1ed38-133">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="1ed38-134">Dosya, öncelikle özel durumları hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ed38-134">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="1ed38-135">Uygulamanızın dosyalarıyla dağıtmak değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ed38-135">You can choose not to distribute it with your application's files.</span></span> <span data-ttu-id="1ed38-136">Uygulamanızın yayın derleme hatalarını ayıklamak istediğiniz olay, ancak kaydedin gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-136">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="1ed38-137">İstediğiniz şekilde uygulama dosyalarında tamamını dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ed38-137">You can deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="1ed38-138">Örneğin, bir ZIP dosyası paketini, basit bir kullanmak `copy` komutunu veya tercih ettiğiniz herhangi bir yükleme paketi ile dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ed38-138">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="1ed38-139">Yüklendikten sonra kullanıcılar, uygulamanızın kullanarak yürütebilirsiniz `dotnet` komutu ve uygulama filename gibi sağlayarak `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="1ed38-139">Once installed, users can execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="1ed38-140">Uygulama ikili dosyaların yanı sıra, yükleyici de paylaşılan framework Yükleyici paketini ya da için uygulama yüklemesinin bir parçası olarak bir önkoşul olarak denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-140">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="1ed38-141">Paylaşılan framework yüklemesi yönetici/kök erişimi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-141">Installation of the shared framework requires Administrator/root access.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="1ed38-142">Üçüncü taraf bağımlılıkları Framework bağımlı dağıtım</span><span class="sxs-lookup"><span data-stu-id="1ed38-142">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="1ed38-143">Bir veya daha fazla üçüncü taraf bağımlılıkları framework bağımlı dağıtım dağıtma bu bağımlılıkların projeniz için kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-143">Deploying a framework-dependent deployment with one or more third-party dependencies requires that those dependencies be available to your project.</span></span> <span data-ttu-id="1ed38-144">Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:</span><span class="sxs-lookup"><span data-stu-id="1ed38-144">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="1ed38-145">Gerekli üçüncü taraf kitaplıklarına başvurular ekleyin `<ItemGroup>` bölümü, *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="1ed38-145">Add references to required third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="1ed38-146">Aşağıdaki `<ItemGroup>` bölüm üzerinde bir bağımlılık içerir [Json.NET](http://www.newtonsoft.com/json) üçüncü taraf kitaplık olarak:</span><span class="sxs-lookup"><span data-stu-id="1ed38-146">The following `<ItemGroup>` section contains a dependency on [Json.NET](http://www.newtonsoft.com/json) as a third-party library:</span></span>

      ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
      ```

1. <span data-ttu-id="1ed38-147">Henüz yapmadıysanız, üçüncü taraf bağımlılığı içeren NuGet paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-147">If you haven't already, download the NuGet package containing the third-party dependency.</span></span> <span data-ttu-id="1ed38-148">Paketini karşıdan yüklemek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu.</span><span class="sxs-lookup"><span data-stu-id="1ed38-148">To download the package, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="1ed38-149">Bağımlılık yerel NuGet önbelleği dışında çözümlendiğinden zaman yayınlamak için sisteminizde kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ed38-149">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="1ed38-150">Üçüncü taraf bağımlılıkları framework bağımlı dağıtımla yalnızca üçüncü taraf bağımlılıkları olarak taşınabilir olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-150">Note that a framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="1ed38-151">Örneğin, bir üçüncü taraf kitaplık yalnızca macOS destekliyorsa, uygulamayı Windows sistemleri için taşınabilir değil.</span><span class="sxs-lookup"><span data-stu-id="1ed38-151">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="1ed38-152">Üçüncü taraf bağımlılığı yerel kodu bağımlı olması durumunda bu gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-152">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="1ed38-153">Bu iyi bir örnektir [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), üzerindeki yerel bir bağımlılık gerektiren [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="1ed38-153">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="1ed38-154">Üçüncü taraf bağımlılığı bu tür bir uygulama için bir FDD oluşturulduğunda, yayımlanan çıktı bir klasör için her içerir [çalışma zamanı tanımlayıcı (RID)](../rid-catalog.md) yerel bağımlılık destekleyen (ve onun NuGet paketi var).</span><span class="sxs-lookup"><span data-stu-id="1ed38-154">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="simpleSelf"></a><span data-ttu-id="1ed38-155">Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtımıdır</span><span class="sxs-lookup"><span data-stu-id="1ed38-155">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="1ed38-156">Üçüncü taraf bağımlılıkları içerir olmadan projesi oluşturma kendi içinde bulunan bir dağıtım dağıtma değiştirme *csproj* dosya oluşturma, test etme ve uygulama yayımlama.</span><span class="sxs-lookup"><span data-stu-id="1ed38-156">Deploying a self-contained deployment without third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="1ed38-157">C# ile yazılmış basit bir örnek işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-157">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="1ed38-158">Örnek kullanarak kendi içinde bulunan dağıtımı oluşturmak nasıl gösterir [dotnet yardımcı programı](../tools/dotnet.md) komut satırından.</span><span class="sxs-lookup"><span data-stu-id="1ed38-158">The example shows how to create a self-contained deployment using the [dotnet utility](../tools/dotnet.md) from the command line.</span></span>

1. <span data-ttu-id="1ed38-159">Proje için bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ed38-159">Create a directory for the project.</span></span>

   <span data-ttu-id="1ed38-160">Projeniz için bir dizin oluşturun ve geçerli dizininiz yapın.</span><span class="sxs-lookup"><span data-stu-id="1ed38-160">Create a directory for your project, and make it your current directory.</span></span>

1. <span data-ttu-id="1ed38-161">Projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ed38-161">Create the project.</span></span>

   <span data-ttu-id="1ed38-162">Komut satırından yazın [dotnet yeni konsol](../tools/dotnet-new.md) bu dizinde yeni bir C# konsol projesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="1ed38-162">From the command line, type [dotnet new console](../tools/dotnet-new.md) to create a new C# console project in that directory.</span></span>

1. <span data-ttu-id="1ed38-163">Uygulamanın kaynak kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-163">Add the application's source code.</span></span>

   <span data-ttu-id="1ed38-164">Açık *Program.cs* dosya düzenleyicinizde ve otomatik olarak oluşturulan kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-164">Open the *Program.cs* file in your editor and replace the auto-generated code with the following code.</span></span> <span data-ttu-id="1ed38-165">Metin girmesini ister ve kullanıcı tarafından girilen ayrı sözcükleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ed38-165">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="1ed38-166">Normal ifade kullanan `\w+` giriş metni sözcükleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="1ed38-166">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. <span data-ttu-id="1ed38-167">Uygulamanızı Hedef platformlar tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="1ed38-167">Define the platforms that your app will target.</span></span>

   <span data-ttu-id="1ed38-168">Oluşturma bir `<RuntimeIdentifiers>` içinde etiketi `<PropertyGroup>` bölümü, *csproj* uygulamanızı hedefler ve hedeflediğiniz her platform için çalışma zamanı tanımlayıcı (RID) belirtin platformları tanımlayan dosyası.</span><span class="sxs-lookup"><span data-stu-id="1ed38-168">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets and specify the runtime identifier (RID) for each platform that you target.</span></span> <span data-ttu-id="1ed38-169">Aynı zamanda RID ayırmak için noktalı virgül eklemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1ed38-169">Note that you also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="1ed38-170">Bkz: [çalışma zamanı tanımlayıcı katalog](../rid-catalog.md) çalışma zamanı tanımlayıcılarının listesi.</span><span class="sxs-lookup"><span data-stu-id="1ed38-170">See [Runtime IDentifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span> 

   <span data-ttu-id="1ed38-171">Örneğin, aşağıdaki `<PropertyGroup>` bölümü gösterir uygulama 64-bit Windows 10 işletim sistemleri ve 64-bit OS X sürüm 10.11 sürümünü işletim sisteminde çalışır.</span><span class="sxs-lookup"><span data-stu-id="1ed38-171">For example, the following `<PropertyGroup>` section indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

     ```xml
     <PropertyGroup>
         <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
     </PropertyGroup>
     ```

   <span data-ttu-id="1ed38-172">Unutmayın `<RuntimeIdentifiers>` öğesi içinde görünebilir `<PropertyGroup>` içinde *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="1ed38-172">Note that the `<RuntimeIdentifiers>` element can appear in any `<PropertyGroup>` in your *csproj* file.</span></span> <span data-ttu-id="1ed38-173">Tam bir örnek *csproj* dosyası bu bölümde daha sonra görünür.</span><span class="sxs-lookup"><span data-stu-id="1ed38-173">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="1ed38-174">Proje bağımlılıkları ve araçları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-174">Update the project's dependencies and tools.</span></span>

   <span data-ttu-id="1ed38-175">Çalıştırma [dotnet geri yükleme](../tools/dotnet-restore.md) ([bkz. Not](#dotnet-restore-note)) projenizde belirtilen bağımlılıkları geri yüklemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="1ed38-175">Run the [dotnet restore](../tools/dotnet-restore.md) ([see note](#dotnet-restore-note)) command to restore the dependencies specified in your project.</span></span>

1. <span data-ttu-id="1ed38-176">Hata ayıklama derlemesi, uygulamanızın oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ed38-176">Create a Debug build of your app.</span></span>

   <span data-ttu-id="1ed38-177">Komut satırından kullanma [dotnet yapı](../tools/dotnet-build.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="1ed38-177">From the command line, use the [dotnet build](../tools/dotnet-build.md) command.</span></span>

1. <span data-ttu-id="1ed38-178">Hata ayıklaması ve program test sonra her platform için uygulamanız ile bu hedefler dağıtılacak dosyaları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1ed38-178">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="1ed38-179">Kullanım `dotnet publish` her ikisi de aşağıdaki gibi platformları hedeflemesi için komut:</span><span class="sxs-lookup"><span data-stu-id="1ed38-179">Use the `dotnet publish` command for both target platforms as follows:</span></span>

      ```console
      dotnet publish -c Release -r win10-x64
      dotnet publish -c Release -r osx.10.11-x64
      ```

   <span data-ttu-id="1ed38-180">Bu sürüm (bir hata ayıklama yerine) oluşturur uygulamanız için her hedef platformu sürümü.</span><span class="sxs-lookup"><span data-stu-id="1ed38-180">This creates a Release (rather than a Debug) version of your app for each target platform.</span></span> <span data-ttu-id="1ed38-181">Ortaya çıkan dosyalar adlı bir alt dizinde yerleştirilir *yayımlama* projenizin bir alt dizin olan *.\bin\Release\netcoreapp1.1\<runtime_identifier >* alt dizin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-181">The resulting files are placed in a subdirectory named *publish* that's in a subdirectory of your project's *.\bin\Release\netcoreapp1.1\<runtime_identifier>* subdirectory.</span></span> <span data-ttu-id="1ed38-182">Her alt uygulamanızı başlatmak için gereken dosyaları (uygulama dosyalarınızı ve tüm .NET Core dosyaları) tam kümesi içerdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1ed38-182">Note that each subdirectory contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="1ed38-183">Uygulamanızın dosyaları yanı sıra, yayımlama işlemi uygulamanız ile ilgili hata ayıklama bilgilerini içeren bir program veritabanı (.pdb) dosyası yayar.</span><span class="sxs-lookup"><span data-stu-id="1ed38-183">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="1ed38-184">Dosya, öncelikle özel durumları hata ayıklama için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="1ed38-184">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="1ed38-185">Bu paket, uygulamanızın dosyaları ile değil seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ed38-185">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="1ed38-186">Uygulamanızın yayın derleme hatalarını ayıklamak istediğiniz olay, ancak kaydedin gerekir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-186">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="1ed38-187">İstediğiniz şekilde yayımlanan dosyalarında dağıtın.</span><span class="sxs-lookup"><span data-stu-id="1ed38-187">Deploy the published files in any way you like.</span></span> <span data-ttu-id="1ed38-188">Örneğin, bir ZIP dosyası paketini, basit bir kullanmak `copy` komutunu veya tercih ettiğiniz herhangi bir yükleme paketi ile dağıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ed38-188">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="1ed38-189">Aşağıdaki tamamlandıktan *csproj* bu proje için dosya.</span><span class="sxs-lookup"><span data-stu-id="1ed38-189">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="1ed38-190">Üçüncü taraf bağımlılıkları kendi içinde bulunan dağıtım</span><span class="sxs-lookup"><span data-stu-id="1ed38-190">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="1ed38-191">Bir veya daha fazla üçüncü taraf bağımlılıkları kendi içinde bulunan bir dağıtım dağıtma bağımlılıkları ekleme içerir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-191">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="1ed38-192">Çalıştırmadan önce iki ek adımlar gerekli `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komutu:</span><span class="sxs-lookup"><span data-stu-id="1ed38-192">Two additional steps are required before you can run the `dotnet restore` ([see note](#dotnet-restore-note)) command:</span></span>

1. <span data-ttu-id="1ed38-193">Tüm üçüncü taraf kitaplıklarına başvurular ekleyin `<ItemGroup>` bölümü, *csproj* dosya.</span><span class="sxs-lookup"><span data-stu-id="1ed38-193">Add references to any third-party libraries to the `<ItemGroup>` section of your *csproj* file.</span></span> <span data-ttu-id="1ed38-194">Aşağıdaki `<ItemGroup>` bölüm Json.NET üçüncü taraf kitaplık olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="1ed38-194">The following `<ItemGroup>` section uses Json.NET as a third-party library.</span></span>

    ```xml
      <ItemGroup>
        <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
      </ItemGroup>
    ```

1. <span data-ttu-id="1ed38-195">Henüz yapmadıysanız, üçüncü taraf bağımlılığı sisteminize içeren NuGet paketini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1ed38-195">If you haven't already, download the NuGet package containing the third-party dependency to your system.</span></span> <span data-ttu-id="1ed38-196">Bağımlılık uygulamanızı kullanılabilir hale getirmek için yürütme `dotnet restore` ([bkz. Not](#dotnet-restore-note)) bağımlılık ekledikten sonra komutu.</span><span class="sxs-lookup"><span data-stu-id="1ed38-196">To make the dependency available to your app, execute the `dotnet restore` ([see note](#dotnet-restore-note)) command after adding the dependency.</span></span> <span data-ttu-id="1ed38-197">Bağımlılık yerel NuGet önbelleği dışında çözümlendiğinden zaman yayınlamak için sisteminizde kullanılabilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1ed38-197">Because the dependency is resolved out of the local NuGet cache at publish time, it must be available on your system.</span></span>

<span data-ttu-id="1ed38-198">Aşağıdaki tamamlandıktan *csproj* dosyası bu proje için:</span><span class="sxs-lookup"><span data-stu-id="1ed38-198">The following is the complete *csproj* file for this project:</span></span>

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

<span data-ttu-id="1ed38-199">Uygulamanızı dağıttığınızda, uygulamanızda kullanılan tüm üçüncü taraf bağımlılıkları ile uygulama dosyalarını da yer alır.</span><span class="sxs-lookup"><span data-stu-id="1ed38-199">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="1ed38-200">Üçüncü taraf kitaplıklar uygulama çalışırken sistemde gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1ed38-200">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="1ed38-201">Yalnızca bir üçüncü taraf kitaplık müstakil dağıtımla bu kitaplığı tarafından desteklenen platformlar dağıtabileceğiniz olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1ed38-201">Note that you can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="1ed38-202">Bu burada yerel bağımlılıkları uygulamanın dağıtıldığı platform ile uyumlu olmalıdır framework bağımlı dağıtımında, üçüncü taraf bağımlılıkları yerel bağımlılıkları ile zorunda benzer.</span><span class="sxs-lookup"><span data-stu-id="1ed38-202">This is similar to having third-party dependencies with native dependencies in a framework-dependent deployment, where the native dependencies must be compatible with the platform to which the app is deployed.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

# <a name="see-also"></a><span data-ttu-id="1ed38-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ed38-203">See also</span></span>

<span data-ttu-id="1ed38-204">[.NET core uygulama dağıtımı](index.md) </span><span class="sxs-lookup"><span data-stu-id="1ed38-204">[.NET Core Application Deployment](index.md) </span></span>  
[<span data-ttu-id="1ed38-205">.NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu</span><span class="sxs-lookup"><span data-stu-id="1ed38-205">.NET Core Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)   


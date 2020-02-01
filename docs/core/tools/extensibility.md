---
title: .NET Core CLI genişletilebilirlik modeli
description: .NET Core CLI nasıl genişletebileceğinizi öğrenin.
ms.date: 04/12/2017
ms.openlocfilehash: 74da895fb3a3f6c77640a2b9a64acdb2894a954b
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920521"
---
# <a name="net-core-cli-extensibility-model"></a><span data-ttu-id="390c4-103">.NET Core CLI genişletilebilirlik modeli</span><span class="sxs-lookup"><span data-stu-id="390c4-103">.NET Core CLI extensibility model</span></span>

<span data-ttu-id="390c4-104">Bu makalede .NET Core CLI genişletebileceğiniz farklı yollar ele alınmaktadır ve bunların her birini hedefleyen senaryolar açıklanacaktır.</span><span class="sxs-lookup"><span data-stu-id="390c4-104">This article covers the different ways you can extend the .NET Core CLI and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="390c4-105">Araçların nasıl kullanılacağı ve farklı araç türlerini nasıl oluşturacağınız hakkında bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-the-cli"></a><span data-ttu-id="390c4-106">CLı 'yı genişletme</span><span class="sxs-lookup"><span data-stu-id="390c4-106">How to extend the CLI</span></span>
<span data-ttu-id="390c4-107">CLı üç ana şekilde genişletilebilir:</span><span class="sxs-lookup"><span data-stu-id="390c4-107">The CLI can be extended in three main ways:</span></span>

1. [<span data-ttu-id="390c4-108">Her proje temelinde NuGet paketleri aracılığıyla</span><span class="sxs-lookup"><span data-stu-id="390c4-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="390c4-109">Proje başına Araçlar, projenin bağlamı içinde bulunur, ancak geri yükleme yoluyla kolayca yüklemeye izin verir.</span><span class="sxs-lookup"><span data-stu-id="390c4-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="390c4-110">Özel hedefleri olan NuGet paketleri aracılığıyla</span><span class="sxs-lookup"><span data-stu-id="390c4-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="390c4-111">Özel hedefler, yapı sürecini özel görevlerle kolayca genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="390c4-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="390c4-112">Sistemin yolu aracılığıyla</span><span class="sxs-lookup"><span data-stu-id="390c4-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="390c4-113">YOL tabanlı araçlar, tek bir makinede kullanılabilen genel, projeler arası araçlar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="390c4-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="390c4-114">Yukarıda özetlenen üç genişletilebilirlik mekanizması dışlamalı değildir.</span><span class="sxs-lookup"><span data-stu-id="390c4-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="390c4-115">Birini veya tümünü veya bunların bir bileşimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="390c4-116">Bunlardan biri, uzantınıza ulaşmayı denediğiniz hedefe büyük ölçüde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="390c4-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="390c4-117">Proje tabanlı genişletilebilirlik</span><span class="sxs-lookup"><span data-stu-id="390c4-117">Per-project based extensibility</span></span>
<span data-ttu-id="390c4-118">Proje başına Araçlar, NuGet paketleri olarak dağıtılan [çerçeveye bağımlı dağıtımlardır](../deploying/index.md#framework-dependent-deployments-fdd) .</span><span class="sxs-lookup"><span data-stu-id="390c4-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="390c4-119">Araçlar yalnızca bunlara başvuran ve bunların geri yüklendiği proje bağlamında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="390c4-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="390c4-120">Proje bağlamı dışında (örneğin, projeyi içeren dizinin dışında) çağırma başarısız olur çünkü komut bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="390c4-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="390c4-121">Bu araçlar, derleme sunucuları için idealdir, çünkü proje dosyası dışında hiçbir şey gerekmez.</span><span class="sxs-lookup"><span data-stu-id="390c4-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="390c4-122">Yapı işlemi, oluşturduğu proje için geri yüklemeyi çalıştırır ve araçlar kullanılabilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="390c4-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="390c4-123">Her proje yalnızca belirli bir F#dilde yazıdıklarından, gibi dil projeleri de bu kategoride yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="390c4-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="390c4-124">Son olarak, bu genişletilebilirlik modeli, projenin oluşturulan çıktısına erişmesi gereken araçların oluşturulmasına yönelik destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="390c4-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="390c4-125">Örneğin, [ASP.net](https://www.asp.net/) MVC uygulamalarındaki çeşitli Razor görünümü araçları bu kategoriye girer.</span><span class="sxs-lookup"><span data-stu-id="390c4-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="390c4-126">Proje başına araçları kullanma</span><span class="sxs-lookup"><span data-stu-id="390c4-126">Consuming per-project tools</span></span>
<span data-ttu-id="390c4-127">Bu araçların kullanılması için, kullanmak istediğiniz her bir araç için proje dosyanıza bir `<DotNetCliToolReference>` öğesi eklemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="390c4-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="390c4-128">`<DotNetCliToolReference>` öğesinin içinde, aracın bulunduğu pakete başvuru ve ihtiyacınız olan sürümü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="390c4-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="390c4-129">[`dotnet restore`](dotnet-restore.md)çalıştırıldıktan sonra araç ve bağımlılıkları geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="390c4-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="390c4-130">Yürütülmesi için projenin yapı çıkışını yüklemesi gereken araçlar için, genellikle proje dosyasındaki normal bağımlılıklar altında listelenen başka bir bağımlılık vardır.</span><span class="sxs-lookup"><span data-stu-id="390c4-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="390c4-131">CLı, yapı altyapısı olarak MSBuild kullandığından, bu aracın bu bölümlerinin özel MSBuild [hedefleri](/visualstudio/msbuild/msbuild-targets) ve [görevleri](/visualstudio/msbuild/msbuild-tasks)olarak yazılması önerilir, çünkü bu, genel derleme sürecinde bir bölüm alabilir.</span><span class="sxs-lookup"><span data-stu-id="390c4-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="390c4-132">Ayrıca, çıkış dosyalarının konumu, oluşturulmakta olan geçerli yapılandırma vb. gibi, yapı aracılığıyla üretilen tüm ve tüm verileri kolayca alabilirler.</span><span class="sxs-lookup"><span data-stu-id="390c4-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, and so on.</span></span> <span data-ttu-id="390c4-133">Tüm bu bilgiler, herhangi bir hedeften okunabilecek bir MSBuild özellikleri kümesi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="390c4-133">All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="390c4-134">Bu belgede daha sonra NuGet kullanarak özel bir hedef ekleme hakkında bilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-134">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="390c4-135">Basit bir projeye basit bir araç öncesi araç ekleme örneğini incelim.</span><span class="sxs-lookup"><span data-stu-id="390c4-135">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="390c4-136">Belirtilen API için NuGet paketlerinde arama yapmanıza olanak sağlayan `dotnet-api-search` adlı örnek bir komut verildiğinde, bu aracı kullanan bir konsol uygulamasının proje dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="390c4-136">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="390c4-137">`<DotNetCliToolReference>` öğesi `<PackageReference>` öğesi gibi benzer bir şekilde yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="390c4-137">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="390c4-138">Geri yükleyebilmek için aracı ve sürümünü içeren paketin paket KIMLIĞI gereklidir.</span><span class="sxs-lookup"><span data-stu-id="390c4-138">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="390c4-139">Araç oluşturma</span><span class="sxs-lookup"><span data-stu-id="390c4-139">Building tools</span></span>
<span data-ttu-id="390c4-140">Belirtildiği gibi, araçlar yalnızca taşınabilir konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="390c4-140">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="390c4-141">Diğer konsol uygulamaları oluştururken araçlar oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="390c4-141">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="390c4-142">Derlemeyi oluşturduktan sonra, kodunuzu içeren bir NuGet paketi (. nupkg dosyası) oluşturmak için [`dotnet pack`](dotnet-pack.md) komutunu, bağımlılıklarıyla ilgili bilgileri ve benzerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="390c4-142">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="390c4-143">Pakete herhangi bir ad verebilirsiniz, ancak gerçek araç ikilisinin içindeki uygulamanın, `dotnet` çağırabilmesi için `dotnet-<command>` kuralına uygun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="390c4-143">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="390c4-144">.NET Core komut satırı araçlarının pre-RC3 sürümlerinde `dotnet pack` komutunda, araçla paketlenmemelidir *. runtimeconfig. JSON* dosyasına neden olan bir hata vardı.</span><span class="sxs-lookup"><span data-stu-id="390c4-144">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the *.runtimeconfig.json* to not be packed with the tool.</span></span> <span data-ttu-id="390c4-145">Bu dosya çalışma zamanında hata oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="390c4-145">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="390c4-146">Bu davranışla karşılaşırsanız, en son araçları güncelleştirdiğinizden emin olun ve `dotnet pack` yeniden deneyin.</span><span class="sxs-lookup"><span data-stu-id="390c4-146">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="390c4-147">Araçlar taşınabilir uygulamalar olduğundan, aracı kullanan kullanıcının aracı çalıştırmak için, aracın oluşturulduğu .NET Core kitaplıklarının sürümüne sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="390c4-147">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="390c4-148">Aracın kullandığı ve .NET Core kitaplıkları içinde bulunmayan diğer tüm bağımlılıklar geri yüklenir ve NuGet önbelleğine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="390c4-148">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="390c4-149">Bu nedenle, tüm araç, .NET Core kütüphanelerinin derlemeleri ve NuGet önbelleğinden derlemelerin kullanılmasıyla çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="390c4-149">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="390c4-150">Bu tür araçların, kendisini kullanan projenin bağımlılık grafiğinden tamamen ayrı olan bir bağımlılık grafiği vardır.</span><span class="sxs-lookup"><span data-stu-id="390c4-150">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="390c4-151">Geri yükleme işlemi öncelikle projenin bağımlılıklarını geri yükler ve ardından araçların her birini ve bağımlılıklarını geri yükler.</span><span class="sxs-lookup"><span data-stu-id="390c4-151">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="390c4-152">[.NET Core CLI](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects)deposunda Bunun daha zengin örnekleri ve farklı birleşimlerini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-152">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="390c4-153">Aynı depoda [kullanılan araçların uygulanmasını](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-153">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

## <a name="custom-targets"></a><span data-ttu-id="390c4-154">Özel hedefler</span><span class="sxs-lookup"><span data-stu-id="390c4-154">Custom targets</span></span>

<span data-ttu-id="390c4-155">NuGet [özel MSBuild hedeflerini ve props dosyalarını paketleme](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="390c4-155">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="390c4-156">MSBuild 'i kullanmak için .NET Core 'un taşınması sayesinde aynı genişletilebilirlik mekanizması artık .NET Core projeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="390c4-156">With the move of the .NET Core to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="390c4-157">Yapı işlemini genişletmek istediğinizde veya oluşturulan dosyalar gibi yapı işlemindeki yapıtlardan herhangi birine erişmek istediğinizde veya yapının çağrıldığı yapılandırmayı incelemek istediğinizde, bu tür bir genişletilebilirlik kullanın vb.</span><span class="sxs-lookup"><span data-stu-id="390c4-157">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, and so on.</span></span>

<span data-ttu-id="390c4-158">Aşağıdaki örnekte, `csproj` sözdizimini kullanarak hedefin proje dosyasını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-158">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="390c4-159">Bu, [`dotnet pack`](dotnet-pack.md) komutuna ne paketlenecek, hedef dosyaların yanı sıra derlemeleri paketin içindeki *Yapı* klasörüne yerleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="390c4-159">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="390c4-160">`Label` özelliği `dotnet pack instructions`olarak ayarlanan `<ItemGroup>` öğeye ve altında tanımlanan hedefe dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="390c4-160">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="390c4-161">Özel hedefleri tüketen, pakete ve genişletilmekte olan projenin içindeki sürümüne işaret eden bir `<PackageReference>` sağlayarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="390c4-161">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="390c4-162">Araçların aksine, özel hedefler paketi, tüketen projenin bağımlılık kapanışına dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="390c4-162">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="390c4-163">Özel hedefin kullanılması yalnızca nasıl yapılandırdığınıza bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="390c4-163">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="390c4-164">Bir MSBuild hedefi olduğundan, belirli bir hedefe bağlı olabilir, başka bir hedeften sonra çalıştırılabilir ve ayrıca `dotnet msbuild -t:<target-name>` komutu kullanılarak el ile çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="390c4-164">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild -t:<target-name>` command.</span></span>

<span data-ttu-id="390c4-165">Ancak kullanıcılarınıza daha iyi bir kullanıcı deneyimi sağlamak istiyorsanız, proje başına araçları ve özel hedefleri birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-165">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="390c4-166">Bu senaryoda, proje başına aracı temel olarak yalnızca gerekli parametreleri kabul eder ve hedefi yürütecek gerekli [`dotnet msbuild`](dotnet-msbuild.md) çağrısına çevirirler.</span><span class="sxs-lookup"><span data-stu-id="390c4-166">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="390c4-167">[`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projesindeki [MVP Zirvesi 2016 Hackathon örnekleri](https://github.com/dotnet/MVPSummitHackathon2016) deposunda bu tür bir sinerjiden bahsederek denemelerini örneğini görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-167">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="path-based-extensibility"></a><span data-ttu-id="390c4-168">YOL tabanlı genişletilebilirlik</span><span class="sxs-lookup"><span data-stu-id="390c4-168">PATH-based extensibility</span></span>
<span data-ttu-id="390c4-169">YOL tabanlı genişletilebilirlik genellikle, kavramsal olarak tek bir projeden daha fazla yer kaplayan bir araca ihtiyacınız olan geliştirme makinelerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="390c4-169">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="390c4-170">Bu uzantı mekanizmasının ana dezavantajı, aracın bulunduğu makineye bağlı olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="390c4-170">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="390c4-171">Başka bir makinede ihtiyacınız varsa dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="390c4-171">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="390c4-172">CLı araç takımı genişletilebilirliği bu düzende çok basittir.</span><span class="sxs-lookup"><span data-stu-id="390c4-172">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="390c4-173">[.NET Core CLI genel bakış](index.md)kapsamında da gösterildiği gibi, `dotnet` sürücü `dotnet-<command>` kuralından sonra adlandırılmış herhangi bir komutu çalıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="390c4-173">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="390c4-174">Varsayılan çözüm mantığı öncelikle birkaç konumu yoklamıştır ve son olarak sistem yoluna geri döner.</span><span class="sxs-lookup"><span data-stu-id="390c4-174">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="390c4-175">İstenen komut sistem yolunda varsa ve çağrılabilecek bir ikili dosyaysa `dotnet` sürücü bunu çağırır.</span><span class="sxs-lookup"><span data-stu-id="390c4-175">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="390c4-176">Dosya yürütülebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="390c4-176">The file must be executable.</span></span> <span data-ttu-id="390c4-177">UNIX sistemlerinde, bu, `chmod +x`aracılığıyla yürütme biti ayarlanmış herhangi bir şey anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="390c4-177">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="390c4-178">Windows 'ta *cmd* dosyalarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-178">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="390c4-179">Bir "Merhaba Dünya" aracının çok basit uygulamasına göz atalım.</span><span class="sxs-lookup"><span data-stu-id="390c4-179">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="390c4-180">Windows üzerinde hem `bash` hem de `cmd` kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="390c4-180">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="390c4-181">Aşağıdaki komut konsola yalnızca "Merhaba Dünya" yankısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="390c4-181">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="390c4-182">MacOS 'ta bu betiği `dotnet-hello` olarak kaydedebilir ve yürütülebilir bitini `chmod +x dotnet-hello`olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-182">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="390c4-183">Daha sonra komut `ln -s <full_path>/dotnet-hello /usr/local/bin/`kullanarak `/usr/local/bin` bir sembolik bağlantı oluşturuyoruz.</span><span class="sxs-lookup"><span data-stu-id="390c4-183">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="390c4-184">Bu, `dotnet hello` söz dizimini kullanarak komutu çağırmayı mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="390c4-184">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="390c4-185">Windows 'ta, bu betiği `dotnet-hello.cmd` olarak kaydedebilir ve sistem yolundaki bir konuma koyabilirsiniz (veya zaten yolda olan bir klasöre ekleyebilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="390c4-185">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="390c4-186">Bundan sonra, bu örneği çalıştırmak için yalnızca `dotnet hello` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="390c4-186">After this, you can just use `dotnet hello` to run this example.</span></span>

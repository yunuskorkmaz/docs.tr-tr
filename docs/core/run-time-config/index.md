---
title: Çalışma zamanı yapılandırma seçenekleri
description: Çalışma zamanı yapılandırma ayarlarını kullanarak .NET Core uygulamalarını nasıl yapılandıracağınızı öğrenin.
ms.date: 01/21/2020
ms.openlocfilehash: 68690689fd4f936e3af76ab647f0b58d8ec6ca27
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761960"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="d1457-103">.NET Core çalışma zamanı yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="d1457-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="d1457-104">.NET Core, çalışma zamanında .NET Core uygulamalarının davranışını yapılandırmak için yapılandırma dosyalarının ve ortam değişkenlerinin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="d1457-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="d1457-105">Çalışma zamanı yapılandırması, şu durumlarda çekici bir seçenektir:</span><span class="sxs-lookup"><span data-stu-id="d1457-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="d1457-106">Bir uygulama için kaynak kodu sahibi değilsiniz veya denetiminiz yoktur, bu nedenle program aracılığıyla yapılandıramamaktır.</span><span class="sxs-lookup"><span data-stu-id="d1457-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="d1457-107">Uygulamanızın birden çok örneği tek bir sistemde aynı anda çalışır ve her birini en iyi performans için yapılandırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="d1457-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="d1457-108">Bu belge devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="d1457-108">This documentation is a work in progress.</span></span> <span data-ttu-id="d1457-109">Burada sunulan bilgilerin eksik veya yanlış olduğunu fark ederseniz, bunun hakkında bilgi sahibi olmak için [bir sorun açın](https://github.com/dotnet/docs/issues) veya sorunu çözmek için [bir çekme isteği gönderin](https://github.com/dotnet/docs/pulls) .</span><span class="sxs-lookup"><span data-stu-id="d1457-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="d1457-110">DotNet/docs deposu için çekme istekleri gönderme hakkında daha fazla bilgi için bkz. [katkıda bulunan Kılavuzu](https://docs.microsoft.com/contribute/dotnet/dotnet-contribute).</span><span class="sxs-lookup"><span data-stu-id="d1457-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://docs.microsoft.com/contribute/dotnet/dotnet-contribute).</span></span>

<span data-ttu-id="d1457-111">.NET Core, çalışma zamanında uygulama davranışını yapılandırmak için aşağıdaki mekanizmaları sağlar:</span><span class="sxs-lookup"><span data-stu-id="d1457-111">.NET Core provides the following mechanisms for configuring application behavior at run time:</span></span>

- <span data-ttu-id="d1457-112">[Runtimeconfig. JSON dosyası](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="d1457-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="d1457-113">MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="d1457-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="d1457-114">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="d1457-114">Environment variables</span></span>](#environment-variables)

> [!TIP]
> <span data-ttu-id="d1457-115">Bir ortam değişkeni kullanarak bir çalışma zamanı seçeneğinin yapılandırılması, ayarı tüm .NET Core uygulamalarına uygular.</span><span class="sxs-lookup"><span data-stu-id="d1457-115">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="d1457-116">*Runtimeconfig. JSON* veya proje dosyasında bir çalışma zamanı seçeneğinin yapılandırılması, ayarı yalnızca bu uygulamaya uygular.</span><span class="sxs-lookup"><span data-stu-id="d1457-116">Configuring a run-time option in the *runtimeconfig.json* or project file applies the setting to that application only.</span></span>

<span data-ttu-id="d1457-117">Bazı yapılandırma değerleri, yöntemi çağırarak programlı bir şekilde ayarlanabilir <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d1457-117">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d1457-118">Belgelerin bu bölümündeki makaleler, bir kategoriye göre düzenlenir, örneğin [hata ayıklama](debugging-profiling.md) ve [çöp toplama](garbage-collector.md).</span><span class="sxs-lookup"><span data-stu-id="d1457-118">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="d1457-119">Uygun olduğunda, yapılandırma seçenekleri için *runtimeconfig. JSON* dosyaları, MSBuild özellikleri, ortam değişkenleri ve .NET Framework projeler için çapraz başvuru, *app. config* dosyaları için gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d1457-119">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="d1457-120">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="d1457-120">runtimeconfig.json</span></span>

<span data-ttu-id="d1457-121">Bir proje [oluşturulduğunda, çıkış](../tools/dotnet-build.md)dizininde *[AppName]. runtimeconfig. JSON* dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d1457-121">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="d1457-122">Proje dosyasıyla aynı klasörde bir *runtimeconfig. Template. JSON* dosyası varsa, içerdiği tüm yapılandırma seçenekleri *[AppName]. runtimeconfig. JSON* dosyasında birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d1457-122">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="d1457-123">Uygulamayı kendiniz oluşturuyorsanız, tüm yapılandırma seçeneklerini *runtimeconfig. Template. JSON* dosyasına koyun.</span><span class="sxs-lookup"><span data-stu-id="d1457-123">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="d1457-124">Uygulamayı yalnızca çalıştırıyorsanız doğrudan *[AppName]. runtimeconfig. JSON* dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1457-124">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="d1457-125">*[AppName]. runtimeconfig. JSON* dosyasının sonraki yapılarda üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="d1457-125">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="d1457-126">*Runtimeconfig. JSON* dosyalarının **ConfigProperties** bölümünde çalışma zamanı yapılandırma seçeneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="d1457-126">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="d1457-127">Bu bölüm şu biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="d1457-127">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="d1457-128">Örnek [AppName]. runtimeconfig. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="d1457-128">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="d1457-129">Seçenekleri çıkış JSON dosyasına yerleştiriyorsanız, özelliğin altına yerleştirin `runtimeOptions` .</span><span class="sxs-lookup"><span data-stu-id="d1457-129">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="d1457-130">Örnek runtimeconfig. Template. JSON dosyası</span><span class="sxs-lookup"><span data-stu-id="d1457-130">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="d1457-131">Seçenekleri şablon JSON dosyasına yerleştiriyorsanız, `runtimeOptions` özelliği atlayın.</span><span class="sxs-lookup"><span data-stu-id="d1457-131">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="d1457-132">MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="d1457-132">MSBuild properties</span></span>

<span data-ttu-id="d1457-133">Bazı çalışma zamanı yapılandırma seçenekleri, SDK stili .NET Core projelerinin *. csproj* veya *. vbproj* dosyasındaki MSBuild özellikleri kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d1457-133">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="d1457-134">MSBuild özellikleri, *runtimeconfig. Template. JSON* dosyasında ayarlanan seçeneklere göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="d1457-134">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="d1457-135">Ayrıca derleme zamanında *[AppName]. runtimeconfig. JSON* dosyasında ayarladığınız seçeneklerin üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="d1457-135">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="d1457-136">Aşağıda, çalışma zamanı davranışını yapılandırmak için MSBuild özelliklerine sahip örnek bir SDK stili proje dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d1457-136">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="d1457-137">Çalışma zamanı davranışını yapılandırmaya yönelik MSBuild özellikleri, her bir alana yönelik her bir makalede (örneğin, [çöp toplama](garbage-collector.md)) belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1457-137">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="d1457-138">Bunlar ayrıca SDK stili projelerin MSBuild özellikleri başvurusunun [çalışma zamanı yapılandırması](../project-sdk/msbuild-props.md#run-time-configuration-properties) bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="d1457-138">They are also listed in the [Run-time configuration](../project-sdk/msbuild-props.md#run-time-configuration-properties) section of the MSBuild properties reference for SDK-style projects.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="d1457-139">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="d1457-139">Environment variables</span></span>

<span data-ttu-id="d1457-140">Ortam değişkenleri, bazı çalışma zamanı yapılandırma bilgilerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1457-140">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="d1457-141">Bir ortam değişkeni kullanarak bir çalışma zamanı seçeneğinin yapılandırılması, ayarı tüm .NET Core uygulamalarına uygular.</span><span class="sxs-lookup"><span data-stu-id="d1457-141">Configuring a run-time option by using an environment variable applies the setting to all .NET Core apps.</span></span> <span data-ttu-id="d1457-142">Ortam değişkenleri olarak belirtilen yapılandırma örneklerinin genellikle **COMPlus_** öneki vardır.</span><span class="sxs-lookup"><span data-stu-id="d1457-142">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="d1457-143">Ortam değişkenlerini Windows Denetim masasından, komut satırında veya <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> yöntemini hem Windows hem de UNIX tabanlı sistemlerde çağırarak programlı bir şekilde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1457-143">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="d1457-144">Aşağıdaki örneklerde, komut satırında bir ortam değişkeninin nasıl ayarlanacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d1457-144">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```

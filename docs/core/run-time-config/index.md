---
title: Çalışma zamanı config seçenekleri
description: Çalışma zamanı yapılandırma ayarlarını kullanarak .NET Core uygulamalarını nasıl yapılandırıştırmayı öğrenin.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399163"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="ab7ba-103">.NET Core çalışma zamanı yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="ab7ba-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="ab7ba-104">.NET Core, .NET Core uygulamalarının davranışını çalışma zamanında yapılandırmak için yapılandırma dosyalarının ve ortam değişkenlerinin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="ab7ba-105">Çalışma zamanı yapılandırması cazip bir seçenektir:</span><span class="sxs-lookup"><span data-stu-id="ab7ba-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="ab7ba-106">Bir uygulamanın kaynak koduna sahip değilsiniz veya denetlemiyorsunuz ve bu nedenle bunu programlı olarak yapılandıramadığınız için.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="ab7ba-107">Uygulamanızın birden çok örneği tek bir sistemde aynı anda çalışır ve her birini optimum performans için yapılandırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="ab7ba-108">Bu belge, devam etmekte olan bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-108">This documentation is a work in progress.</span></span> <span data-ttu-id="ab7ba-109">Burada sunulan bilgilerin eksik veya yanlış olduğunu fark ederseniz, bu konuda bize bildirmek için [bir sorun açın](https://github.com/dotnet/docs/issues) veya sorunu gidermek için bir çekme isteği [gönderin.](https://github.com/dotnet/docs/pulls)</span><span class="sxs-lookup"><span data-stu-id="ab7ba-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="ab7ba-110">dotnet/docs deposu için çekme istekleri gönderme hakkında bilgi için [katılımcının kılavuzuna](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-110">For information about submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="ab7ba-111">.NET Core, çalışma zamanı uygulama davranışını yapılandırmak için aşağıdaki mekanizmaları sağlar:</span><span class="sxs-lookup"><span data-stu-id="ab7ba-111">.NET Core provides the following mechanisms for configuring run-time application behavior:</span></span>

- <span data-ttu-id="ab7ba-112">[Runtimeconfig.json dosyası](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="ab7ba-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="ab7ba-113">MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="ab7ba-113">MSBuild properties</span></span>](#msbuild-properties)

- [<span data-ttu-id="ab7ba-114">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ab7ba-114">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="ab7ba-115">Bazı yapılandırma değerleri de <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntem çağırarak programlı olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-115">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ab7ba-116">Belgelerin bu bölümündeki makaleler kategoriye göre düzenlenir, örneğin, [hata ayıklama](debugging-profiling.md) ve [çöp toplama.](garbage-collector.md)</span><span class="sxs-lookup"><span data-stu-id="ab7ba-116">The articles in this section of the documentation are organized by category, for example, [debugging](debugging-profiling.md) and [garbage collection](garbage-collector.md).</span></span> <span data-ttu-id="ab7ba-117">Uygulanabilir olduğu durumlarda, *runtimeconfig.json* dosyaları, MSBuild özellikleri, ortam değişkenleri ve çapraz başvuru için .NET Framework projeleri için *app.config* dosyaları için yapılandırma seçenekleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-117">Where applicable, configuration options are shown for *runtimeconfig.json* files, MSBuild properties, environment variables, and, for cross-reference, *app.config* files for .NET Framework projects.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="ab7ba-118">runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="ab7ba-118">runtimeconfig.json</span></span>

<span data-ttu-id="ab7ba-119">Bir proje [oluşturulduğunda,](../tools/dotnet-build.md)çıktı dizininde bir *[appname].runtimeconfig.json* dosyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-119">When a project is [built](../tools/dotnet-build.md), an *[appname].runtimeconfig.json* file is generated in the output directory.</span></span> <span data-ttu-id="ab7ba-120">*Runtimeconfig.template.json* dosyası proje dosyasıyla aynı klasörde varsa, içerdiği tüm yapılandırma seçenekleri *[appname].runtimeconfig.json* dosyasında birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-120">If a *runtimeconfig.template.json* file exists in the same folder as the project file, any configuration options it contains are merged into the *[appname].runtimeconfig.json* file.</span></span> <span data-ttu-id="ab7ba-121">Uygulamayı kendiniz oluşturuyorsanız, *runtimeconfig.template.json* dosyasına herhangi bir yapılandırma seçeneği koyun.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-121">If you're building the app yourself, put any configuration options in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="ab7ba-122">Uygulamayı çalıştırıyorsanız, doğrudan *[appname].runtimeconfig.json* dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-122">If you're just running the app, insert them directly into the *[appname].runtimeconfig.json* file.</span></span>

> [!NOTE]
> <span data-ttu-id="ab7ba-123">*[appname].runtimeconfig.json* dosyası sonraki yapılarda üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-123">The *[appname].runtimeconfig.json* file will get overwritten on subsequent builds.</span></span>

<span data-ttu-id="ab7ba-124">*Runtimeconfig.json* dosyalarının **configProperties** bölümünde çalışma zamanı yapılandırma seçeneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-124">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* files.</span></span> <span data-ttu-id="ab7ba-125">Bu bölümde şu form vardır:</span><span class="sxs-lookup"><span data-stu-id="ab7ba-125">This section has the form:</span></span>

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a><span data-ttu-id="ab7ba-126">Örnek [appname].runtimeconfig.json dosyası</span><span class="sxs-lookup"><span data-stu-id="ab7ba-126">Example [appname].runtimeconfig.json file</span></span>

<span data-ttu-id="ab7ba-127">Seçenekleri çıktı JSON dosyasına yerlebir ediyorsanız, `runtimeOptions` bunları özelliğin altına yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-127">If you're placing the options in the output JSON file, nest them under the `runtimeOptions` property.</span></span>

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

### <a name="example-runtimeconfigtemplatejson-file"></a><span data-ttu-id="ab7ba-128">Örnek runtimeconfig.template.json dosyası</span><span class="sxs-lookup"><span data-stu-id="ab7ba-128">Example runtimeconfig.template.json file</span></span>

<span data-ttu-id="ab7ba-129">Seçenekleri şablon JSON dosyasına yerlesanız, özelliği atleyin. `runtimeOptions`</span><span class="sxs-lookup"><span data-stu-id="ab7ba-129">If you're placing the options in the template JSON file, omit the `runtimeOptions` property.</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a><span data-ttu-id="ab7ba-130">MSBuild özellikleri</span><span class="sxs-lookup"><span data-stu-id="ab7ba-130">MSBuild properties</span></span>

<span data-ttu-id="ab7ba-131">Bazı çalışma zamanı yapılandırma seçenekleri, SDK stili .NET Core projelerinin *.csproj* veya *.vbproj* dosyasındaki MSBuild özellikleri kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-131">Some run-time configuration options can be set using MSBuild properties in the *.csproj* or *.vbproj* file of SDK-style .NET Core projects.</span></span> <span data-ttu-id="ab7ba-132">MSBuild özellikleri *runtimeconfig.template.json* dosyasında ayarlanan seçeneklerden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-132">MSBuild properties take precedence over options set in the *runtimeconfig.template.json* file.</span></span> <span data-ttu-id="ab7ba-133">*Ayrıca,[appname].runtimeconfig.json* dosyasında ayarladığınız seçeneklerin üzerine de yazılırlar.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-133">They also overwrite any options you set in the *[appname].runtimeconfig.json* file at build time.</span></span>

<span data-ttu-id="ab7ba-134">Çalışma zamanı davranışını yapılandırmak için MSBuild özelliklerine sahip örnek bir SDK tarzı proje dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ab7ba-134">Here is an example SDK-style project file with MSBuild properties for configuring run-time behavior:</span></span>

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

<span data-ttu-id="ab7ba-135">Çalışma zamanı davranışını yapılandırmak için MSBuild özellikleri, çöp [toplama](garbage-collector.md)gibi her alan için ayrı ayrı makalelerde belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-135">MSBuild properties for configuring run-time behavior are noted in the individual articles for each area, for example, [garbage collection](garbage-collector.md).</span></span>

## <a name="environment-variables"></a><span data-ttu-id="ab7ba-136">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ab7ba-136">Environment variables</span></span>

<span data-ttu-id="ab7ba-137">Ortam değişkenleri bazı çalışma zamanı yapılandırma bilgileri sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-137">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="ab7ba-138">Çevre değişkenleri olarak belirtilen yapılandırma düğümleri genellikle **COMPlus_** önekine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-138">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="ab7ba-139">Ortam değişkenlerini Windows Denetim Masası'ndan, komut satırından veya programlı <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> olarak hem Windows hem de Unix tabanlı sistemlerde arayarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab7ba-139">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="ab7ba-140">Aşağıdaki örnekler, komut satırında bir ortam değişkeninin nasıl ayarlangerektiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="ab7ba-140">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```

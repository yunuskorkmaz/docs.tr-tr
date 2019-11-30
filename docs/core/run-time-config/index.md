---
title: Çalışma zamanı yapılandırması
description: Çalışma zamanı yapılandırma ayarlarını kullanarak .NET Core uygulamalarını nasıl yapılandıracağınızı öğrenin.
ms.date: 11/13/2019
ms.openlocfilehash: e3922f6df81198b5e122f16d5cfc4b6d15cbb4ae
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567384"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="79029-103">.NET Core çalışma zamanı yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="79029-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="79029-104">.NET Core, çalışma zamanında .NET Core uygulamalarının davranışını yapılandırmak için yapılandırma dosyalarının ve ortam değişkenlerinin kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="79029-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="79029-105">Çalışma zamanı yapılandırması, şu durumlarda çekici bir seçenektir:</span><span class="sxs-lookup"><span data-stu-id="79029-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="79029-106">Bir uygulama için kaynak kodu sahibi değilsiniz veya denetiminiz yoktur, bu nedenle program aracılığıyla yapılandıramamaktır.</span><span class="sxs-lookup"><span data-stu-id="79029-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="79029-107">Uygulamanızın birden çok örneği tek bir sistemde aynı anda çalışır ve her birini en iyi performans için yapılandırmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="79029-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="79029-108">Bu belge devam eden bir çalışmadır.</span><span class="sxs-lookup"><span data-stu-id="79029-108">This documentation is a work in progress.</span></span> <span data-ttu-id="79029-109">Burada sunulan bilgilerin eksik veya yanlış olduğunu fark ederseniz, bunun hakkında bilgi sahibi olmak için [bir sorun açın](https://github.com/dotnet/docs/issues) veya sorunu çözmek için [bir çekme isteği gönderin](https://github.com/dotnet/docs/pulls) .</span><span class="sxs-lookup"><span data-stu-id="79029-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="79029-110">DotNet/docs deposu için çekme istekleri gönderme hakkında daha fazla bilgi için bkz. [katkıda bulunan Kılavuzu](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="79029-110">For information on submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="79029-111">.NET Core, çalışma zamanında uygulamaları yapılandırmak için aşağıdaki mekanizmaları sağlar:</span><span class="sxs-lookup"><span data-stu-id="79029-111">.NET Core provides the following mechanisms for configuring applications at run time:</span></span>

- <span data-ttu-id="79029-112">[Runtimeconfig. JSON dosyası](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="79029-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="79029-113">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="79029-113">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="79029-114">Belgelerin bu bölümündeki makaleler, örneğin, hata ayıklama ve çöp toplama gibi kategoriye göre düzenlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="79029-114">The articles in this section of the documentation include are organized by category, for example, debugging and garbage collection.</span></span> <span data-ttu-id="79029-115">Kullanılabilir yapılandırma seçenekleri, *runtimeconfig. JSON* (yalnızca .NET Core), *app. config* (yalnızca .NET Framework) ve ortam değişkenleri için gösterilir.</span><span class="sxs-lookup"><span data-stu-id="79029-115">Available configuration options are shown for *runtimeconfig.json* (.NET Core only), *app.config* (.NET Framework only), and environment variables.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="79029-116">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="79029-116">runtimeconfig.json</span></span>

<span data-ttu-id="79029-117">*Runtimeconfig. JSON* dosyasının **ConfigProperties** bölümünde çalışma zamanı yapılandırma seçeneklerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="79029-117">Specify run-time configuration options in the **configProperties** section of the *runtimeconfig.json* file.</span></span> <span data-ttu-id="79029-118">Bu bölüm şu biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="79029-118">This section has the form:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

<span data-ttu-id="79029-119">Örnek bir dosya aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="79029-119">Here is an example file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

<span data-ttu-id="79029-120">*Runtimeconfig. JSON* dosyası, [DotNet Build](../tools/dotnet-build.md) komutuyla derleme dizininde otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="79029-120">The *runtimeconfig.json* file is automatically created in the build directory by the [dotnet build](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="79029-121">Visual Studio 'da **Build** Menu seçeneğini belirlediğinizde de oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="79029-121">It's also created when you select the **Build** menu option in Visual Studio.</span></span> <span data-ttu-id="79029-122">Sonra dosyayı, oluşturulduktan sonra düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79029-122">You can then edit the file once it's created.</span></span>

<span data-ttu-id="79029-123">Bazı yapılandırma değerleri de <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi çağırarak programlı olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="79029-123">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="79029-124">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="79029-124">Environment variables</span></span>

<span data-ttu-id="79029-125">Ortam değişkenleri, bazı çalışma zamanı yapılandırma bilgilerini sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="79029-125">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="79029-126">Ortam değişkenleri olarak belirtilen yapılandırma örneklerinin genellikle **COMPlus_** öneki vardır.</span><span class="sxs-lookup"><span data-stu-id="79029-126">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="79029-127">Ortam değişkenlerini Windows Denetim masasından, komut satırında veya <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> yöntemini hem Windows hem de UNIX tabanlı sistemlerde çağırarak programlı bir şekilde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79029-127">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="79029-128">Aşağıdaki örneklerde, komut satırında bir ortam değişkeninin nasıl ayarlanacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="79029-128">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```

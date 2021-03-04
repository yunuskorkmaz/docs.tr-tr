---
title: "NETSDK1045: geçerli .NET SDK, hedef olarak ' yeni sürümü ' desteklemez."
description: Derleme araçları .NET SDK 'nın istenen sürümünü bulamadığında oluşan .NET SDK hatası NETSDK1045 hakkında bilgi edinin.
ms.topic: error-reference
ms.date: 02/12/2021
f1_keywords:
- NETSDK1045
ms.openlocfilehash: 7f21270fdc7c2db862a49302a302bf8121fc86a5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104108"
---
# <a name="netsdk1045-the-current-net-sdk-does-not-support-newer-version-as-a-target"></a><span data-ttu-id="78c2b-103">NETSDK1045: geçerli .NET SDK, hedef olarak ' yeni sürümü ' desteklemez.</span><span class="sxs-lookup"><span data-stu-id="78c2b-103">NETSDK1045: The current .NET SDK does not support 'newer version' as a target.</span></span>

<span data-ttu-id="78c2b-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="78c2b-104">**This article applies to:** ✔️ .NET Core 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="78c2b-105">Bu hata, derleme araçları bir proje oluşturmak için gereken .NET SDK sürümünü bulamadığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="78c2b-105">This error occurs when the build tools can't find the version of the .NET SDK that's needed to build a project.</span></span> <span data-ttu-id="78c2b-106">Bunun nedeni genellikle .NET Core SDK yükleme veya yapılandırma sorunudur.</span><span class="sxs-lookup"><span data-stu-id="78c2b-106">This is typically due to a .NET Core SDK installation or configuration issue.</span></span> <span data-ttu-id="78c2b-107">Tam hata iletisi aşağıdaki örneğe benzer:</span><span class="sxs-lookup"><span data-stu-id="78c2b-107">The full error message is similar to the following example:</span></span>

> <span data-ttu-id="78c2b-108">NETSDK1045: geçerli .NET SDK, hedef olarak ' yeni sürümü ' desteklemez.</span><span class="sxs-lookup"><span data-stu-id="78c2b-108">NETSDK1045: The current .NET SDK does not support 'newer version' as a target.</span></span> <span data-ttu-id="78c2b-109">' Daha eski sürümü ' veya daha düşük bir sürüm ya da ' daha yeni sürümü destekleyen bir .NET SDK sürümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="78c2b-109">Either target 'older version' or lower, or use a .NET SDK version that supports 'newer version'.</span></span>

<span data-ttu-id="78c2b-110">Aşağıdaki bölümlerde bu hatanın bazı olası nedenleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="78c2b-110">The following sections describe some of the possible reasons for this error.</span></span> <span data-ttu-id="78c2b-111">Her birini işaretleyin ve hangisinin sizin için geçerli olduğunu görün.</span><span class="sxs-lookup"><span data-stu-id="78c2b-111">Check each one and see which one applies to you.</span></span> <span data-ttu-id="78c2b-112">Ortamda veya yapılandırma dosyalarında değişiklik yaparken, değişikliklerinizin etkili olması için komut pencerelerini yeniden başlatmanız, Visual Studio 'yu yeniden başlatmanız veya makinenizi yeniden başlatmanız gerektiğini aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="78c2b-112">Keep in mind that when making changes to the environment or the configuration files, you might have to restart command windows, restart Visual Studio, or reboot your machine, for your changes to take effect.</span></span>

## <a name="net-sdk-version"></a><span data-ttu-id="78c2b-113">.NET SDK sürümü</span><span class="sxs-lookup"><span data-stu-id="78c2b-113">.NET SDK version</span></span>

<span data-ttu-id="78c2b-114">Proje dosyasını (. csproj,. vbproj veya. fsproj) açın ve hedef çerçeveyi denetleyin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-114">Open the project file (.csproj, .vbproj, or .fsproj) and check the target framework.</span></span> <span data-ttu-id="78c2b-115">Bu, uygulamanızın kullanmaya çalıştığı çerçevenin sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="78c2b-115">This is the version of the framework that your app is trying to use.</span></span>

```xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

<span data-ttu-id="78c2b-116">Listelenen .NET sürümünün makinede yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="78c2b-116">Make sure that the version of .NET listed is installed on the machine.</span></span> <span data-ttu-id="78c2b-117">Yüklü sürümleri aşağıdaki komutu kullanarak listeleyebilir (bir Geliştirici Komut İstemi açın ve bu komutu çalıştırın):</span><span class="sxs-lookup"><span data-stu-id="78c2b-117">You can list the installed versions by using the following command (open a Developer Command Prompt and run this command):</span></span>

```dotnetcli
dotnet --list-sdks
```

### <a name="x86-or-x64-architecture"></a><span data-ttu-id="78c2b-118">x86 veya x64 mimarisi</span><span class="sxs-lookup"><span data-stu-id="78c2b-118">x86 or x64 architecture</span></span>

<span data-ttu-id="78c2b-119">.NET SDK 'sının her sürümü hem x86 hem de x64 mimarisinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="78c2b-119">Each version of the .NET SDK is available in both x86 and x64 architecture.</span></span> <span data-ttu-id="78c2b-120">Proje, yanlış mimaride .NET SDK 'yı bulmaya çalışıyor veya projenizin ihtiyaç duyacağı mimariye yönelik .NET SDK 'Sı yüklenmemiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="78c2b-120">The project might be trying to find the .NET SDK for the wrong architecture, or the .NET SDK for the architecture your project needs might not be installed.</span></span> <span data-ttu-id="78c2b-121">İhtiyacınız olan mimarinin yükleme klasörlerini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-121">Check the installation folders for the architecture you need.</span></span> <span data-ttu-id="78c2b-122">Örneğin, Windows 'ta, .NET SDK 'nın x86 sürümü *C:\Program Files (x86) \dotnet* ' ye yüklenir ve x64 sürümü *c:\Program files\dotnet* dizinine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="78c2b-122">For example, on Windows, the x86 version of the .NET SDK is installed in *C:\Program Files (x86)\dotnet* and the x64 version is installed in *C:\Program Files\dotnet*.</span></span> <span data-ttu-id="78c2b-123">Bkz. [.net 'in zaten yüklü olduğunu denetleme](../../install/how-to-detect-installed-versions.md) ve makinenizde nelerin yüklü olduğunu nasıl algılayabileceğinizi öğrenmek için işletim sisteminizi seçin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-123">See [How to check that .NET is already installed](../../install/how-to-detect-installed-versions.md) and choose your operating system to find out how to detect what's installed on your machine.</span></span>

<span data-ttu-id="78c2b-124">İhtiyacınız olan sürüm yüklü değilse, [.net İndirmeleri](https://dotnet.microsoft.com/download/dotnet) sayfasında ihtiyacınız olan birini bulun.</span><span class="sxs-lookup"><span data-stu-id="78c2b-124">If the version you need isn't installed, find the one you need at the [.NET Downloads](https://dotnet.microsoft.com/download/dotnet) page.</span></span>

## <a name="preview-not-enabled"></a><span data-ttu-id="78c2b-125">Önizleme etkin değil</span><span class="sxs-lookup"><span data-stu-id="78c2b-125">Preview not enabled</span></span>

<span data-ttu-id="78c2b-126">İstenen .NET SDK sürümünün yüklü olduğu bir önizlemeye sahipseniz, Visual Studio 'da önizlemeleri etkinleştirme seçeneğini de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="78c2b-126">If you have a preview installed of the requested .NET SDK version, you also need to set the option to enable previews in Visual Studio.</span></span> <span data-ttu-id="78c2b-127">**Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri**' ne gidin ve **.NET Core SDK Önizlemesi ' nin** işaretli olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="78c2b-127">Go to **Tools** > **Options** > **Environment** > **Preview Features**, and make sure that **Use previews of the .NET Core SDK** is checked.</span></span>

## <a name="visual-studio-version"></a><span data-ttu-id="78c2b-128">Visual Studio sürüm</span><span class="sxs-lookup"><span data-stu-id="78c2b-128">Visual Studio version</span></span>

<span data-ttu-id="78c2b-129">Örneğin, .NET Core 3,0 ve üzeri Visual Studio 2019 gerektirir.</span><span class="sxs-lookup"><span data-stu-id="78c2b-129">For example, .NET Core 3.0 and later require Visual Studio 2019.</span></span> <span data-ttu-id="78c2b-130">Projenizi derlemek için [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads) veya sonraki bir sürüme yükseltin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-130">Upgrade to [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads) or later to build your project.</span></span>

## <a name="path-environment-variable"></a><span data-ttu-id="78c2b-131">PATH ortam değişkeni</span><span class="sxs-lookup"><span data-stu-id="78c2b-131">PATH environment variable</span></span>

<span data-ttu-id="78c2b-132">Yapı araçları, .NET derleme araçlarının doğru sürümünü bulmak için PATH ortam değişkenini kullanır.</span><span class="sxs-lookup"><span data-stu-id="78c2b-132">The build tools use the PATH environment variable to find the right version of the .NET build tools.</span></span> <span data-ttu-id="78c2b-133">PATH ortam değişkeni eski derleme araçlarına doğrudan yollar içeriyorsa, bu hata iletisi görünebilir.</span><span class="sxs-lookup"><span data-stu-id="78c2b-133">If the PATH environment variable contains direct paths to older build tools, this error message could appear.</span></span> <span data-ttu-id="78c2b-134">PATH ortam değişkeninde .NET araçlarının tek yolunun en üst düzey *DotNet* klasörüne (örneğin, *C:\Program files\dotnet*) ait olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="78c2b-134">Make sure the only path to the .NET tools in the PATH environment variable is to the top-level *dotnet* folder, for example, *C:\Program Files\dotnet*.</span></span> <span data-ttu-id="78c2b-135">Yanlış bir yol örneği, *C:\Program Files\dotnet\2.1.0\sdks* gibi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="78c2b-135">An example of an incorrect PATH would be something like *C:\Program Files\dotnet\2.1.0\sdks*.</span></span>

## <a name="msbuildsdkpath-environment-variable"></a><span data-ttu-id="78c2b-136">MSBuildSDKPath ortam değişkeni</span><span class="sxs-lookup"><span data-stu-id="78c2b-136">MSBuildSDKPath environment variable</span></span>

<span data-ttu-id="78c2b-137">MSBuildSDKPath ortam değişkenini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-137">Check the MSBuildSDKPath environment variable.</span></span> <span data-ttu-id="78c2b-138">Bu isteğe bağlı ortam değişkeni MSBuild tarafından tanınır ve ayarlandıysa, varsayılan değeri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="78c2b-138">This optional environment variable is recognized by MSBuild and if set, overrides the default value.</span></span> <span data-ttu-id="78c2b-139">.NET SDK 'sının belirli bir eski sürümüne ayarlanmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="78c2b-139">It might be set to a specific older version of the .NET SDK.</span></span> <span data-ttu-id="78c2b-140">Ayarlanırsa, projeyi silmeyi ve projenizi yeniden oluşturmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-140">If it's set, try deleting it and rebuilding your project.</span></span>

## <a name="globaljson-file"></a><span data-ttu-id="78c2b-141">Dosya üzerinde global.js</span><span class="sxs-lookup"><span data-stu-id="78c2b-141">global.json file</span></span>

<span data-ttu-id="78c2b-142">Klasör yapısında herhangi bir yerde olduğundan, projenizdeki kök klasördeki birglobal.jsve Dizin zincirini birimin köküne *göre* denetleyin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-142">Check for a *global.json* file in the root folder in your project and up the directory chain to the root of the volume, since it can be anywhere in the folder structure.</span></span> <span data-ttu-id="78c2b-143">Bir SDK sürümü içeriyorsa, `sdk` düğümü ve tüm alt öğelerini silin veya istediğiniz daha yeni .NET Core sürümüne güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-143">If it contains an SDK version, delete the `sdk` node and all its children, or update it to the desired newer .NET Core version.</span></span>

```json
{
  "sdk": {
    "version": "2.1.0"
  }
}
```

<span data-ttu-id="78c2b-144">Dosyadaki *global.js* gerekli değildir, bu nedenle düğüm dışında bir şey içermiyorsa `sdk` dosyanın tamamını silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="78c2b-144">The *global.json* file is not required, so if it doesn't contain anything other than the `sdk` node, you can delete the whole file.</span></span>

## <a name="directorybuildprops-file"></a><span data-ttu-id="78c2b-145">Directory. Build. props dosyası</span><span class="sxs-lookup"><span data-stu-id="78c2b-145">Directory.build.props file</span></span>

<span data-ttu-id="78c2b-146">*Directory. Build. props* dosyası, genel özellikleri ayarlayasağlayan isteğe bağlı bir MSBuild dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="78c2b-146">The *Directory.build.props* file is an optional MSBuild file that can set global properties.</span></span> <span data-ttu-id="78c2b-147">Bu dosyaları çözüm klasöründe ve Dizin zincirini birimin köküne, klasör yapısında herhangi bir yerde olabilecekleri şekilde denetleyin.</span><span class="sxs-lookup"><span data-stu-id="78c2b-147">Check for these files in the solution folder and up the directory chain to the root of the volume, since they can be anywhere in the folder structure.</span></span> <span data-ttu-id="78c2b-148">`TargetFramework` `MSBuildSDKPath` İstediğiniz ayarları geçersiz kılabileceğiniz öğeleri veya ayarlarını bulun.</span><span class="sxs-lookup"><span data-stu-id="78c2b-148">Look for `TargetFramework` elements, or settings of `MSBuildSDKPath` that could override your desired settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="78c2b-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78c2b-149">See also</span></span>

- [<span data-ttu-id="78c2b-150">Geçerli .NET SDK 'Sı .NET Core 3,0 'yi belirlemeyi desteklemiyor – çözüm</span><span class="sxs-lookup"><span data-stu-id="78c2b-150">The Current .NET SDK does not support targeting .NET Core 3.0 – Fix</span></span>](https://www.ryadel.com/current-net-sdk-not-support-net-core-3-0-fix/)

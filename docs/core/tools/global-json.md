---
title: global.json’a genel bakış
description: .NET Core CLI komutlarını çalıştırırken .NET Core SDK sürümünü ayarlamak için Global. json dosyasını nasıl kullanacağınızı öğrenin.
ms.date: 12/03/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 4da703266e98b209cdd031f4ea856b4d7c83930c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714167"
---
# <a name="globaljson-overview"></a><span data-ttu-id="c5450-103">global.json’a genel bakış</span><span class="sxs-lookup"><span data-stu-id="c5450-103">global.json overview</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

<span data-ttu-id="c5450-104">*Global. JSON* dosyası, .NET Core CLI komutlarını çalıştırdığınızda hangi .NET Core SDK sürümünün kullanıldığını tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5450-104">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="c5450-105">.NET Core SDK seçilmesi, projenizin hedeflediği çalışma zamanını belirtmekten bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="c5450-105">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="c5450-106">.NET Core SDK sürümü .NET Core CLI araçlarının hangi sürümlerinin kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5450-106">The .NET Core SDK version indicates which versions of the .NET Core CLI tools are used.</span></span> <span data-ttu-id="c5450-107">Genel olarak, araçların en son sürümünü kullanmak istersiniz, bu yüzden *Global. JSON* dosyası gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c5450-107">In general, you want to use the latest version of the tools, so no *global.json* file is needed.</span></span>

<span data-ttu-id="c5450-108">Bunun yerine çalışma zamanının belirtilmesi hakkında daha fazla bilgi için bkz. [hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c5450-108">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="c5450-109">.NET Core SDK geçerli çalışma dizininde (proje diziniyle aynı olmayan) veya üst dizinlerinden biri olan *Global. JSON* dosyasını arar.</span><span class="sxs-lookup"><span data-stu-id="c5450-109">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="c5450-110">Global. JSON şeması</span><span class="sxs-lookup"><span data-stu-id="c5450-110">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="c5450-111">sdk</span><span class="sxs-lookup"><span data-stu-id="c5450-111">sdk</span></span>

<span data-ttu-id="c5450-112">Tür: nesne</span><span class="sxs-lookup"><span data-stu-id="c5450-112">Type: Object</span></span>

<span data-ttu-id="c5450-113">Seçilecek .NET Core SDK hakkındaki bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5450-113">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="c5450-114">sürümü</span><span class="sxs-lookup"><span data-stu-id="c5450-114">version</span></span>

<span data-ttu-id="c5450-115">Türü: Dize</span><span class="sxs-lookup"><span data-stu-id="c5450-115">Type: String</span></span>

<span data-ttu-id="c5450-116">Kullanılacak .NET Core SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="c5450-116">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="c5450-117">Bu alanın şu şekilde olduğunu unutmayın:</span><span class="sxs-lookup"><span data-stu-id="c5450-117">Note that this field:</span></span>

- <span data-ttu-id="c5450-118">Glob desteği yoktur, yani tam sürüm numarası belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c5450-118">Doesn't have globbing support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="c5450-119">Sürüm aralıklarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c5450-119">Doesn't support version ranges.</span></span>

<span data-ttu-id="c5450-120">Aşağıdaki örnek, bir *Global. JSON* dosyasının içeriğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="c5450-120">The following example shows the contents of a *global.json* file:</span></span>

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="c5450-121">Global. JSON ve .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="c5450-121">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="c5450-122">*Global. JSON* dosyasında bir tane ayarlamak için hangi sürümlerin kullanılabildiğini bilmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="c5450-122">It's helpful to know which versions are available in order to set one in the *global.json* file.</span></span> <span data-ttu-id="c5450-123">Desteklenen kullanılabilir SDK 'ların tam listesini [.NET Core](https://dotnet.microsoft.com/download/dotnet-core) ' u indirin sayfasından bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5450-123">You can find the full list of supported available SDKs at the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span> <span data-ttu-id="c5450-124">.NET Core 2,1 SDK ile başlayarak, makinenizde zaten yüklü olan SDK sürümlerini doğrulamak için aşağıdaki komutu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5450-124">Starting with .NET Core 2.1 SDK, you can run the following command to verify which SDK versions are already installed on your machine:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="c5450-125">Makinenize ek .NET Core SDK sürümleri yüklemek için [.NET Core 'U indir](https://dotnet.microsoft.com/download/dotnet-core) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="c5450-125">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="c5450-126">Aşağıdaki örneğe benzer şekilde, [DotNet New](dotnet-new.md) komutunu yürüterek geçerli dizinde yeni bir *Global. JSON* dosyası oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c5450-126">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a><span data-ttu-id="c5450-127">Eşleşen kurallar</span><span class="sxs-lookup"><span data-stu-id="c5450-127">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="c5450-128">Eşleşen kurallar, .NET Core çalışma zamanının bir parçası olan apphost tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="c5450-128">The matching rules are governed by the apphost, which is part of the .NET Core runtime.</span></span>
> <span data-ttu-id="c5450-129">Ana bilgisayarın en son sürümü, yan yana birden fazla çalışma zamanı yüklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5450-129">The latest version of the host is used when you have multiple runtimes installed side-by-side.</span></span>

<span data-ttu-id="c5450-130">.NET Core 2,0 ile başlayarak, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="c5450-130">Starting with .NET Core 2.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="c5450-131">*Global. JSON* dosyası bulunmazsa veya *geneldir. JSON* bir SDK sürümü belirtmez, en son yüklenen SDK sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5450-131">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="c5450-132">En son SDK sürümü yayın veya yayın öncesi olabilir. en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="c5450-132">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>
- <span data-ttu-id="c5450-133">*Global. JSON* bir SDK sürümü belirtirseniz:</span><span class="sxs-lookup"><span data-stu-id="c5450-133">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="c5450-134">Makinede belirtilen SDK sürümü bulunursa, bu tam sürüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5450-134">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="c5450-135">Makinede belirtilen SDK sürümü bulunamazsa, bu sürümün en son yüklenen SDK **düzeltme eki sürümü** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5450-135">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="c5450-136">En son yüklenen SDK **düzeltme eki sürümü** sürüm veya yayın öncesi olabilir. en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="c5450-136">Latest installed SDK **patch version** can be either release or pre-release - the highest version number wins.</span></span> <span data-ttu-id="c5450-137">.NET Core 2,1 ve üzeri sürümlerde, belirtilen **Düzeltme Eki sürümünden** düşük olan **yama sürümleri** SDK seçiminde yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c5450-137">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="c5450-138">Belirtilen SDK sürümü ve uygun bir SDK **yaması sürümü** bulunamazsa hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="c5450-138">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="c5450-139">SDK sürümü şu anda aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="c5450-139">The SDK version is currently composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="c5450-140">.NET Core SDK **özellik sürümü** , SDK sürümleri 2.1.100 ve üzeri için sayının (`xyz`) son parçasında ilk basamak (`x`) ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="c5450-140">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="c5450-141">Genel olarak, .NET Core SDK .NET Core 'dan daha hızlı bir yayın döngüsüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="c5450-141">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="c5450-142">**Düzeltme eki sürümü** , SDK sürümleri 2.1.100 ve üzeri için sayının (`xyz`) son bölümünde son iki basamak (`yz`) tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c5450-142">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="c5450-143">Örneğin, SDK sürümü olarak `2.1.300` belirtirseniz, SDK seçimi en fazla `2.1.399` bulur ancak `2.1.400` `2.1.300`için bir düzeltme eki sürümü olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="c5450-143">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="c5450-144">`2.1.201` aracılığıyla `2.1.100` .NET Core SDK sürümler sürüm numarası şemaları arasındaki geçiş sırasında yayımlanmıştır ve `xyz` gösterimini doğru şekilde işlemez.</span><span class="sxs-lookup"><span data-stu-id="c5450-144">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="c5450-145">Bu sürümleri *Global. JSON* dosyasında belirtirseniz, belirtilen sürümlerin hedef makinelerde olduğundan emin olmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="c5450-145">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

<span data-ttu-id="c5450-146">.NET Core SDK 1. x ile bir sürüm belirttiyseniz ve tam eşleşme bulunmazsa, en son yüklenen SDK sürümü kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5450-146">With .NET Core SDK 1.x, if you specified a version and no exact match was found, the latest installed SDK version was used.</span></span> <span data-ttu-id="c5450-147">En son SDK sürümü yayın veya yayın öncesi olabilir. en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="c5450-147">Latest SDK version can be either release or pre-release - the highest version number wins.</span></span>

## <a name="troubleshooting-build-warnings"></a><span data-ttu-id="c5450-148">Derleme uyarıları sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="c5450-148">Troubleshooting build warnings</span></span>

> [!WARNING]
> <span data-ttu-id="c5450-149">.NET Core SDK bir önizleme sürümü ile çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="c5450-149">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="c5450-150">SDK sürümünü geçerli projedeki Global. JSON dosyası aracılığıyla tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5450-150">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="c5450-151">Daha fazla <https://go.microsoft.com/fwlink/?linkid=869452></span><span class="sxs-lookup"><span data-stu-id="c5450-151">More at <https://go.microsoft.com/fwlink/?linkid=869452></span></span>

<span data-ttu-id="c5450-152">Bu uyarı, projenizin, [eşleşen kurallar](#matching-rules) bölümünde açıklandığı gibi .NET Core SDK bir önizleme sürümü kullanılarak derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5450-152">This warning indicates that your project is being compiled using a preview version of the .NET Core SDK, as explained in the [Matching rules](#matching-rules) section.</span></span> <span data-ttu-id="c5450-153">.NET Core SDK sürümlerde yüksek kaliteli bir geçmiş ve taahhüt vardır.</span><span class="sxs-lookup"><span data-stu-id="c5450-153">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="c5450-154">Ancak, bir önizleme sürümü kullanmak istemiyorsanız, hangi SDK sürümünün kullanılacağını belirtmek için proje hiyerarşisi yapısına bir *Global. JSON* dosyası ekleyin ve sürümün makinenizde yüklü olduğunu onaylamak için `dotnet --list-sdks` kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5450-154">However, if you don't want to use a preview version, add a *global.json* file to your project hierarchy structure to specify which SDK version to use, and use `dotnet --list-sdks` to confirm that the version is installed on your machine.</span></span> <span data-ttu-id="c5450-155">Yeni bir sürüm yayınlandığında, yeni sürümü kullanmak için *Global. JSON* dosyasını kaldırın veya daha yeni sürümü kullanacak şekilde güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="c5450-155">When a new version is released, to use the new version, either remove the *global.json* file or update it to use the newer version.</span></span>

> [!WARNING]
> <span data-ttu-id="c5450-156">' {StartupProject} ' başlangıç projesi Framework 'ü hedefliyor. NETCoreApp ' sürümü ' {targetFrameworkVersion} '.</span><span class="sxs-lookup"><span data-stu-id="c5450-156">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="c5450-157">Entity Framework Core .NET komut satırı araçlarının bu sürümü yalnızca sürüm 2,0 veya üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="c5450-157">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="c5450-158">Araçların eski sürümlerini kullanma hakkında daha fazla bilgi için bkz. <https://go.microsoft.com/fwlink/?linkid=871254></span><span class="sxs-lookup"><span data-stu-id="c5450-158">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254></span></span>

<span data-ttu-id="c5450-159">.NET Core 2,1 SDK (sürüm 2.1.300) ile başlayarak, `dotnet ef` komutu SDK 'ya dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="c5450-159">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="c5450-160">Bu uyarı, projenizin .NET Core 2,1 SDK ve sonraki sürümlerle uyumlu olmayan EF Core 1,0 veya 1,1 ' i hedeflediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c5450-160">This warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions.</span></span> <span data-ttu-id="c5450-161">Projenizi derlemek için, makinenizde .NET Core 2,0 SDK (sürüm 2.1.201) ve önceki bir sürümü yükleyip *Global. JSON* dosyasını kullanarak istenen SDK sürümünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="c5450-161">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) and earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="c5450-162">`dotnet ef` komutu hakkında daha fazla bilgi için bkz. [EF Core .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="c5450-162">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="c5450-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5450-163">See also</span></span>

- [<span data-ttu-id="c5450-164">Proje SDK 'Ları nasıl çözümlenir</span><span class="sxs-lookup"><span data-stu-id="c5450-164">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)

---
title: global.json’a genel bakış
description: .NET Core CLI komutlarını çalıştırırken .NET Core SDK sürümünü ayarlamak için global.json dosyasını nasıl kullanacağınızı öğrenin.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 70257566e1ff30f5c97212a5e0e3c308c27738b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626001"
---
# <a name="globaljson-overview"></a><span data-ttu-id="28a82-103">global.json’a genel bakış</span><span class="sxs-lookup"><span data-stu-id="28a82-103">global.json overview</span></span>

<span data-ttu-id="28a82-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="28a82-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="28a82-105">*global.json* dosyası, .NET Core CLI komutlarını çalıştırdığınızda hangi .NET Core SDK sürümünün kullanıldığını tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="28a82-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="28a82-106">.NET Core SDK'yı seçmek, proje hedeflerinizi çalışma zamanı olarak belirtmekten bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="28a82-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="28a82-107">.NET Core SDK sürümü .NET Core CLI'nin hangi sürümlerinin kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28a82-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="28a82-108">Genel olarak, SDK araçlarının en son sürümünü kullanmak istiyorsunuz, bu nedenle *global.json* dosyası gerekmez.</span><span class="sxs-lookup"><span data-stu-id="28a82-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="28a82-109">Bazı gelişmiş senaryolarda, SDK araçlarının sürümünü denetlemek isteyebilirsiniz ve bu makalede bunun nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="28a82-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="28a82-110">Bunun yerine çalışma zamanı belirtme hakkında daha fazla bilgi için [Hedef çerçeveleri'ne](../../standard/frameworks.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="28a82-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="28a82-111">.NET Core SDK, geçerli çalışma dizininde (proje dizini ile aynı olmayan) veya ana dizinde bir *global.json* dosyası arar.</span><span class="sxs-lookup"><span data-stu-id="28a82-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="28a82-112">global.json şema</span><span class="sxs-lookup"><span data-stu-id="28a82-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="28a82-113">sdk</span><span class="sxs-lookup"><span data-stu-id="28a82-113">sdk</span></span>

<span data-ttu-id="28a82-114">Türü:`object`</span><span class="sxs-lookup"><span data-stu-id="28a82-114">Type: `object`</span></span>

<span data-ttu-id="28a82-115">Seçmek için .NET Core SDK hakkında bilgi belirtir.</span><span class="sxs-lookup"><span data-stu-id="28a82-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="28a82-116">version</span><span class="sxs-lookup"><span data-stu-id="28a82-116">version</span></span>

- <span data-ttu-id="28a82-117">Türü:`string`</span><span class="sxs-lookup"><span data-stu-id="28a82-117">Type: `string`</span></span>

- <span data-ttu-id="28a82-118">Şu andan itibaren kullanılabilir: .NET Core 1.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="28a82-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="28a82-119">.NET Core SDK sürümü kullanmak.</span><span class="sxs-lookup"><span data-stu-id="28a82-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="28a82-120">Bu alan:</span><span class="sxs-lookup"><span data-stu-id="28a82-120">This field:</span></span>

- <span data-ttu-id="28a82-121">Joker karakter desteği yok, yani tam sürüm numarası belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="28a82-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="28a82-122">Sürüm aralıklarını desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="28a82-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="28a82-123">izinPrerelease</span><span class="sxs-lookup"><span data-stu-id="28a82-123">allowPrerelease</span></span>

- <span data-ttu-id="28a82-124">Türü:`boolean`</span><span class="sxs-lookup"><span data-stu-id="28a82-124">Type: `boolean`</span></span>

- <span data-ttu-id="28a82-125">Şu andan itibaren kullanılabilir: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="28a82-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="28a82-126">SDK çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümleri ni göz önünde bulundurup göz önünde bulundurmaması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="28a82-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="28a82-127">Bu değeri açıkça ayarlamazsanız, varsayılan değer Visual Studio'dan çalışıp çalışmadığınıza bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="28a82-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="28a82-128">Visual Studio'da **değilseniz,** varsayılan değer `true`.</span><span class="sxs-lookup"><span data-stu-id="28a82-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="28a82-129">Visual Studio'daysanız, istenen yayın öncesi durumu kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="28a82-130">Diğer bir zamanda, Visual Studio'nun Önizleme sürümünü kullanıyorsanız veya **.NET Core SDK seçeneğinin Kullanım önizlemelerini** **(Araç** >  `true`**Seçenekleri** > **Ortamı** > Önizleme**Özellikleri**altında) ayarlarsanız, varsayılan değer; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="28a82-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="28a82-131">Rollforward</span><span class="sxs-lookup"><span data-stu-id="28a82-131">rollForward</span></span>

- <span data-ttu-id="28a82-132">Türü:`string`</span><span class="sxs-lookup"><span data-stu-id="28a82-132">Type: `string`</span></span>

- <span data-ttu-id="28a82-133">Şu andan itibaren kullanılabilir: .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="28a82-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="28a82-134">Bir SDK sürümünü seçerken kullanılacak roll-forward ilkesi, belirli bir SDK sürümü eksikolduğunda veya daha yüksek bir sürümü kullanma yönergesi olarak geri dönüş olarak.</span><span class="sxs-lookup"><span data-stu-id="28a82-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="28a82-135">Bir [sürüm,](#version) `latestMajor`'ye `rollForward` ayarlıyorsanız, bir değerle belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="28a82-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="28a82-136">Kullanılabilir ilkeleri ve davranışlarını anlamak için, biçimdeki `x.y.znn`bir SDK sürümü için aşağıdaki tanımları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="28a82-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="28a82-137">`x`ana sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="28a82-137">`x` is the major version.</span></span>
- <span data-ttu-id="28a82-138">`y`küçük versiyonudur.</span><span class="sxs-lookup"><span data-stu-id="28a82-138">`y` is the minor version.</span></span>
- <span data-ttu-id="28a82-139">`z`özellik grubudur.</span><span class="sxs-lookup"><span data-stu-id="28a82-139">`z` is the feature band.</span></span>
- <span data-ttu-id="28a82-140">`nn`yama sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="28a82-140">`nn` is the patch version.</span></span>

<span data-ttu-id="28a82-141">Aşağıdaki `rollForward` tablo, anahtar için olası değerleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="28a82-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="28a82-142">Değer</span><span class="sxs-lookup"><span data-stu-id="28a82-142">Value</span></span>         | <span data-ttu-id="28a82-143">Davranış</span><span class="sxs-lookup"><span data-stu-id="28a82-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="28a82-144">Belirtilen sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-144">Uses the specified version.</span></span> <br> <span data-ttu-id="28a82-145">Bulunamazsa, en son yama düzeyine doğru yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="28a82-146">Bulunmazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="28a82-147">Bu değer, SDK'nın önceki sürümlerindeki eski davranıştır.</span><span class="sxs-lookup"><span data-stu-id="28a82-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="28a82-148">Belirtilen büyük, minör ve özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="28a82-149">Bulunamazsa, aynı ana/minör içindeki bir sonraki yüksek özellik bandına doğru yuvarlanır ve bu özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="28a82-150">Bulunmazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="28a82-151">Belirtilen büyük, minör ve özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="28a82-152">Bulunamazsa, aynı ana/küçük sürümdeki bir sonraki yüksek özellik bandına doğru ilerler ve bu özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="28a82-153">Bulunamazsa, aynı ana daldaki bir sonraki yüksek minör ve özellik bandına doğru ilerler ve bu özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="28a82-154">Bulunmazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="28a82-155">Belirtilen büyük, minör ve özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="28a82-156">Bulunamazsa, aynı ana/küçük sürümdeki bir sonraki yüksek özellik bandına doğru ilerler ve bu özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="28a82-157">Bulunamazsa, aynı ana daldaki bir sonraki yüksek minör ve özellik bandına doğru ilerler ve bu özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="28a82-158">Bulunamazsa, bir sonraki yüksek büyük, minör ve özellik bandına doğru yuvarlanır ve bu özellik bandı için en son yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="28a82-159">Bulunmazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="28a82-160">İstenen büyük, minör ve özellik bandını yama düzeyiyle eşleştiren ve belirtilen değerden daha büyük veya eşit olan en son yüklü yama düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="28a82-161">Bulunmazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="28a82-162">İstenen büyük ve küçük bantla eşleşen en yüksek yüklü özellik bandını ve yama düzeyini, belirtilen değerden büyük veya eşit bir özellik bandıyla kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="28a82-163">Bulunmazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="28a82-164">İstenen büyük le eşleşen en yüksek yüklü küçük, özellik bandını ve yama düzeyini, belirtilen değerden büyük veya eşit olan bir küçükle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="28a82-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="28a82-165">Bulunmazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="28a82-166">En yüksek yüklü .NET Core SDK'yı, belirtilen değerden büyük veya eşit bir ana ile kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="28a82-167">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="28a82-168">İlerleme kaydetmiyor.</span><span class="sxs-lookup"><span data-stu-id="28a82-168">Doesn't roll forward.</span></span> <span data-ttu-id="28a82-169">Tam eşleşme gerekli.</span><span class="sxs-lookup"><span data-stu-id="28a82-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="28a82-170">Örnekler</span><span class="sxs-lookup"><span data-stu-id="28a82-170">Examples</span></span>

<span data-ttu-id="28a82-171">Aşağıdaki örnek, yayın öncesi sürümlerin nasıl kullanılmaydığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="28a82-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="28a82-172">Aşağıdaki örnek, belirtilen sürümden daha büyük veya eşit olan yüklü en yüksek sürümün nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="28a82-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="28a82-173">Aşağıdaki örnekte, tam olarak belirtilen sürümün nasıl kullanılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="28a82-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="28a82-174">Aşağıdaki örnek, belirli bir sürümün yüklü en yüksek yama sürümünün nasıl kullanılacağını gösterir (formda, 3.1.1xx):</span><span class="sxs-lookup"><span data-stu-id="28a82-174">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="28a82-175">global.json ve .NET Çekirdek CLI</span><span class="sxs-lookup"><span data-stu-id="28a82-175">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="28a82-176">*Global.json* dosyasında bir tane ayarlamak için makinenize hangi SDK sürümlerinin yüklenmiş olduğunu bilmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="28a82-176">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="28a82-177">Bunun nasıl yapılacılaştırılabildiği hakkında daha fazla bilgi için [,.NET Core'](../install/how-to-detect-installed-versions.md#check-sdk-versions)un zaten yüklü olduğundan düşünü</span><span class="sxs-lookup"><span data-stu-id="28a82-177">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="28a82-178">Makinenize ek .NET Core SDK sürümleri yüklemek için [İndir .NET Core](https://dotnet.microsoft.com/download/dotnet-core) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="28a82-178">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="28a82-179">Aşağıdaki örneğe benzer [şekilde dotnet yeni](dotnet-new.md) komutunu çalıştırarak geçerli dizinde yeni bir *global.json* dosyası oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="28a82-179">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="28a82-180">Eşleşen kurallar</span><span class="sxs-lookup"><span data-stu-id="28a82-180">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="28a82-181">Eşleşen kurallar, yüklü olan `dotnet.exe` tüm .NET Core yüklü çalışma zamanlarında yaygın olan giriş noktası tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="28a82-181">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="28a82-182">.NET Core Runtime'ın en son yüklenen sürümünün eşleşen kuralları, yan yana yüklenen birden çok çalışma zamanı olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28a82-182">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="28a82-183">.NET Çekirdek 3.x</span><span class="sxs-lookup"><span data-stu-id="28a82-183">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="28a82-184">.NET Core 3.0 ile başlayarak, SDK'nın hangi sürümünü kullanacağını belirlerken aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="28a82-184">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="28a82-185">*Global.json* dosyası bulunmazsa veya *global.json* bir SDK sürümü veya `allowPrerelease` bir değer belirtmezse, en yüksek yüklü SDK sürümü kullanılır (ayar `rollForward` değeri). `latestMajor`</span><span class="sxs-lookup"><span data-stu-id="28a82-185">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="28a82-186">Yayın öncesi SDK sürümlerinin nasıl `dotnet` çağrıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="28a82-186">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="28a82-187">Visual Studio'da **değilseniz,** ön sürüm sürümleri dikkate alınır.</span><span class="sxs-lookup"><span data-stu-id="28a82-187">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="28a82-188">Visual Studio'daysanız, istenen yayın öncesi durumu kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-188">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="28a82-189">Diğer bir de, Visual Studio'nun Önizleme sürümünü kullanıyorsanız veya **.NET Core SDK seçeneğinin Kullanım önizlemelerini** **(Araç** > **Seçenekleri** > **Ortamı** > Önizleme**Özellikleri**altında) ayarlarsanız, ön sürüm sürümleri dikkate alınır; aksi takdirde, yalnızca sürüm sürümleri dikkate alınır.</span><span class="sxs-lookup"><span data-stu-id="28a82-189">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="28a82-190">Bir *global.json* dosyası sdk sürümünü belirtmez ancak bir `allowPrerelease` değer belirtir bulunursa, en yüksek yüklü SDK sürümü `rollForward` `latestMajor`kullanılır (ayar eşdeğeri).</span><span class="sxs-lookup"><span data-stu-id="28a82-190">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="28a82-191">En son SDK sürümünün serbest bırakılıp yayınlanamayacağı `allowPrerelease`veya yayın öncesi olup olmadığı, sönme nin değerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="28a82-191">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="28a82-192">`true`ön sürüm sürümlerinin dikkate alınagösterdiğini gösterir; `false` yalnızca sürüm sürümlerinin dikkate alındığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28a82-192">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="28a82-193">*Global.json* dosyası bulunursa ve bir SDK sürümü belirtirse:</span><span class="sxs-lookup"><span data-stu-id="28a82-193">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="28a82-194">Değer `rollFoward` ayarlı değilse, `latestPatch` varsayılan `rollForward` ilke olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-194">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="28a82-195">Aksi takdirde, [rollForward](#rollforward) bölümünde her değeri ve davranışlarını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="28a82-195">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="28a82-196">Yayın öncesi sürüm sürümlerinin dikkate alınıp `allowPrerelease` alınmadığı ve ayarlanmadığında varsayılan davranışın ne olduğu [izin verilen Ön sürüm](#allowprerelease) bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="28a82-196">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="28a82-197">.NET Çekirdek 2.x</span><span class="sxs-lookup"><span data-stu-id="28a82-197">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="28a82-198">.NET Core 2.x SDK'da, SDK'nın hangi sürümünü kullanacağı belirlenirken aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="28a82-198">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="28a82-199">*Global.json* dosyası bulunmazsa veya *global.json* bir SDK sürümü belirtmezse, en son yüklenen SDK sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28a82-199">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="28a82-200">En son SDK sürümü serbest veya ön sürüm olabilir - en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-200">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="28a82-201">*global.json* bir SDK sürümü belirtmezse:</span><span class="sxs-lookup"><span data-stu-id="28a82-201">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="28a82-202">Belirtilen SDK sürümü makinede bulunursa, bu tam sürüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28a82-202">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="28a82-203">Belirtilen SDK sürümü makinede bulunamazsa, bu sürümün en son yüklenen SDK **yama sürümü** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="28a82-203">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="28a82-204">En son yüklenen SDK **yama sürümü** serbest bırakılabilir veya ön sürüm olabilir - en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-204">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="28a82-205">.NET Core 2.1 ve üzeri sürümlerde, belirtilen **yama sürümünden** daha düşük **yama sürümleri** SDK seçiminde yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="28a82-205">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="28a82-206">Belirtilen SDK sürümü ve uygun bir SDK **yama sürümü** bulunamazsa, bir hata atılır.</span><span class="sxs-lookup"><span data-stu-id="28a82-206">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="28a82-207">SDK sürümü aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="28a82-207">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="28a82-208">.NET Core SDK'nın **özellik sürümü,** SDK`x`2.1.100 ve`xyz`üzeri sürümler için sayının son bölümündeki () ilk basamak ( ) ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="28a82-208">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="28a82-209">Genel olarak, .NET Core SDK.NET Core'dan daha hızlı bir sürüm döngüsüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="28a82-209">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="28a82-210">**Yama sürümü,** SDK sürümleri 2.1.100 ve üzeri için sayının son bölümündeki`yz`(`xyz`) son iki basamakla tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="28a82-210">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="28a82-211">Örneğin, SDK `2.1.300` sürümü olarak belirtirseniz, SDK seçimi `2.1.399` `2.1.400` kadar bulur ancak için `2.1.300`bir yama sürümü olarak kabul etmez .</span><span class="sxs-lookup"><span data-stu-id="28a82-211">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="28a82-212">.NET Core SDK sürümleri `2.1.100` sürüm `2.1.201` numarası düzenleri arasında geçiş sırasında yayımlandı `xyz` ve gösterimi doğru şekilde işlemez.</span><span class="sxs-lookup"><span data-stu-id="28a82-212">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="28a82-213">Bu sürümleri *global.json* dosyasında belirtmenizi, belirtilen sürümlerin hedef makinelerde olduğundan emin olmamızı şiddetle öneririz.</span><span class="sxs-lookup"><span data-stu-id="28a82-213">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="28a82-214">Yapı uyarılarını giderme</span><span class="sxs-lookup"><span data-stu-id="28a82-214">Troubleshoot build warnings</span></span>

* <span data-ttu-id="28a82-215">Aşağıdaki uyarı, projenizin .NET Core SDK'nın ön sürüm sürümü kullanılarak derlenmiş olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="28a82-215">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="28a82-216">.NET Core SDK'nın önizleme sürümüyle çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="28a82-216">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="28a82-217">Geçerli projedeki global.json dosyası aracılığıyla SDK sürümünü tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28a82-217">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="28a82-218">Daha <https://go.microsoft.com/fwlink/?linkid=869452>fazla .</span><span class="sxs-lookup"><span data-stu-id="28a82-218">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="28a82-219">.NET Core SDK versiyonları yüksek kalitede bir geçmişe ve bağlılığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="28a82-219">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="28a82-220">Ancak, bir ön sürüm sürümü kullanmak istemiyorsanız, [.NET](#allowprerelease) Core 3.0 SDK veya izin Önceki Sürüm bölümünde daha sonraki bir sürümü ile kullanabileceğiniz farklı stratejileri kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="28a82-220">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="28a82-221">.NET Core 3.0 veya daha yüksek Çalışma Süresi veya SDK yüklü hiç makineleri için, bir *global.json* dosyası oluşturmak ve kullanmak istediğiniz tam sürümünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="28a82-221">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="28a82-222">Aşağıdaki uyarı, projenizin .NET Core 2.1 SDK ve sonraki sürümlerle uyumlu olmayan EF Core 1.0 veya 1.1'i hedeflediğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="28a82-222">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="28a82-223">Başlangıç projesi '{startupProject}' hedefleri çerçevesi'. NETCoreApp' sürümü '{targetFrameworkVersion}'.</span><span class="sxs-lookup"><span data-stu-id="28a82-223">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="28a82-224">Entity Framework Core .NET Komut satırı Araçları'nın bu sürümü yalnızca sürüm 2.0 veya daha yüksek destekler.</span><span class="sxs-lookup"><span data-stu-id="28a82-224">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="28a82-225">Araçların eski sürümlerini kullanma hakkında <https://go.microsoft.com/fwlink/?linkid=871254>bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="28a82-225">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="28a82-226">.NET Core 2.1 SDK (sürüm 2.1.300) ile başlayan `dotnet ef` komut, SDK'ya dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="28a82-226">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="28a82-227">Projenizi derlemek için .NET Core 2.0 SDK (sürüm 2.1.201) veya daha önce makinenize yükleyin ve *global.json* dosyasını kullanarak istenen SDK sürümünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="28a82-227">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="28a82-228">`dotnet ef` Komut hakkında daha fazla bilgi [için, BKZ.](/ef/core/miscellaneous/cli/dotnet)</span><span class="sxs-lookup"><span data-stu-id="28a82-228">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="28a82-229">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28a82-229">See also</span></span>

- [<span data-ttu-id="28a82-230">Proje SDK'ları nasıl çözülür?</span><span class="sxs-lookup"><span data-stu-id="28a82-230">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)

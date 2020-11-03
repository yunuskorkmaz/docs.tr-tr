---
title: global.json’a genel bakış
description: .NET Core CLI komutlarını çalıştırırken .NET Core SDK sürümünü ayarlamak için global.jsdosyasını nasıl kullanacağınızı öğrenin.
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 714e32ec841cee214f801de65bccf0041af66b0b
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281551"
---
# <a name="globaljson-overview"></a><span data-ttu-id="efe6b-103">global.json’a genel bakış</span><span class="sxs-lookup"><span data-stu-id="efe6b-103">global.json overview</span></span>

<span data-ttu-id="efe6b-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="efe6b-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="efe6b-105">*global.jsdosyadaki* , .NET Core CLI komutlarını çalıştırdığınızda hangi .NET Core SDK sürümünün kullanıldığını tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="efe6b-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="efe6b-106">.NET Core SDK seçilmesi, projenizin hedeflediği çalışma zamanını belirtmekten bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="efe6b-107">.NET Core SDK sürümü .NET Core CLI hangi sürümlerinin kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="efe6b-108">Genel olarak, SDK araçlarının en son sürümünü kullanmak istiyorsunuz, bu nedenle dosya *üzerindeglobal.js* gerekmez.</span><span class="sxs-lookup"><span data-stu-id="efe6b-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="efe6b-109">Bazı Gelişmiş senaryolarda, SDK araçlarının sürümünü denetlemek isteyebilirsiniz ve bu makalede bunun nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="efe6b-110">Bunun yerine çalışma zamanının belirtilmesi hakkında daha fazla bilgi için bkz. [hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="efe6b-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="efe6b-111">.NET Core SDK geçerli çalışma dizinindeki dosyanın bir *global.js* (proje diziniyle aynı olması gerekmez) veya üst dizinlerinden birine bakar.</span><span class="sxs-lookup"><span data-stu-id="efe6b-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="efe6b-112">Şemada global.js</span><span class="sxs-lookup"><span data-stu-id="efe6b-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="efe6b-113">sdk</span><span class="sxs-lookup"><span data-stu-id="efe6b-113">sdk</span></span>

<span data-ttu-id="efe6b-114">Türüyle `object`</span><span class="sxs-lookup"><span data-stu-id="efe6b-114">Type: `object`</span></span>

<span data-ttu-id="efe6b-115">Seçilecek .NET Core SDK hakkındaki bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="efe6b-116">sürüm</span><span class="sxs-lookup"><span data-stu-id="efe6b-116">version</span></span>

- <span data-ttu-id="efe6b-117">Türüyle `string`</span><span class="sxs-lookup"><span data-stu-id="efe6b-117">Type: `string`</span></span>

- <span data-ttu-id="efe6b-118">Şu tarihten itibaren kullanılabilir: .NET Core 1,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="efe6b-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="efe6b-119">Kullanılacak .NET Core SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="efe6b-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="efe6b-120">Bu alan:</span><span class="sxs-lookup"><span data-stu-id="efe6b-120">This field:</span></span>

- <span data-ttu-id="efe6b-121">Joker karakter desteği yoktur, yani tam sürüm numarası belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="efe6b-122">Sürüm aralıklarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="efe6b-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="efe6b-123">Allowönsürümü</span><span class="sxs-lookup"><span data-stu-id="efe6b-123">allowPrerelease</span></span>

- <span data-ttu-id="efe6b-124">Türüyle `boolean`</span><span class="sxs-lookup"><span data-stu-id="efe6b-124">Type: `boolean`</span></span>

- <span data-ttu-id="efe6b-125">Şu tarihten itibaren kullanılabilir: .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="efe6b-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="efe6b-126">SDK Çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümlerini düşünmesinin gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="efe6b-127">Bu değeri açıkça ayarlamazsanız, varsayılan değer Visual Studio 'dan çalıştırıp çalıştırdığınıza bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="efe6b-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="efe6b-128">Visual Studio 'da **değilseniz** varsayılan değer olur `true` .</span><span class="sxs-lookup"><span data-stu-id="efe6b-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="efe6b-129">Visual Studio 'da çalışıyorsanız, istenen ön sürüm durumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="efe6b-130">Diğer bir deyişle, Visual Studio 'nun önizleme sürümünü kullanıyorsanız veya .NET Core SDK seçeneğinin ( **Araçlar** **Use previews of the .NET Core SDK**  >  **Seçenekler**  >  **ortamı**  >  **Önizleme özellikleri** altında) kullanım önizlemelerini ayarlarsanız, varsayılan değer olur `true` ; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="efe6b-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features** ), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="efe6b-131">Ileri alınmaya</span><span class="sxs-lookup"><span data-stu-id="efe6b-131">rollForward</span></span>

- <span data-ttu-id="efe6b-132">Türüyle `string`</span><span class="sxs-lookup"><span data-stu-id="efe6b-132">Type: `string`</span></span>

- <span data-ttu-id="efe6b-133">Şu tarihten itibaren kullanılabilir: .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="efe6b-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="efe6b-134">Bir SDK sürümü seçerken kullanılacak geri alma ilkesi, belirli bir SDK sürümü eksik olduğunda geri dönüş olarak veya daha yüksek bir sürümü kullanmak için bir yönerge olarak.</span><span class="sxs-lookup"><span data-stu-id="efe6b-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="efe6b-135">Bir [Sürüm](#version) `rollForward` , olarak ayarlamadıkça bir değer ile belirtilmelidir `latestMajor` .</span><span class="sxs-lookup"><span data-stu-id="efe6b-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>
<span data-ttu-id="efe6b-136">Varsayılan ileri alma davranışı, [eşleşen kurallara](#matching-rules)göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-136">The default roll forward behavior is determined by the [matching rules](#matching-rules).</span></span>

<span data-ttu-id="efe6b-137">Kullanılabilir ilkeleri ve bunların davranışlarını anlamak için şu biçimdeki SDK sürümü için aşağıdaki tanımları göz önünde bulundurun `x.y.znn` :</span><span class="sxs-lookup"><span data-stu-id="efe6b-137">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="efe6b-138">`x` ana sürümdür.</span><span class="sxs-lookup"><span data-stu-id="efe6b-138">`x` is the major version.</span></span>
- <span data-ttu-id="efe6b-139">`y` , ikincil sürümdür.</span><span class="sxs-lookup"><span data-stu-id="efe6b-139">`y` is the minor version.</span></span>
- <span data-ttu-id="efe6b-140">`z` , özellik bantdır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-140">`z` is the feature band.</span></span>
- <span data-ttu-id="efe6b-141">`nn` Düzeltme Eki sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="efe6b-141">`nn` is the patch version.</span></span>

<span data-ttu-id="efe6b-142">Aşağıdaki tabloda anahtar için olası değerler gösterilmektedir `rollForward` :</span><span class="sxs-lookup"><span data-stu-id="efe6b-142">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="efe6b-143">Değer</span><span class="sxs-lookup"><span data-stu-id="efe6b-143">Value</span></span>         | <span data-ttu-id="efe6b-144">Davranış</span><span class="sxs-lookup"><span data-stu-id="efe6b-144">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="efe6b-145">Belirtilen sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-145">Uses the specified version.</span></span> <br> <span data-ttu-id="efe6b-146">Bulunamazsa, en son düzeltme eki düzeyine doğru kaydeder.</span><span class="sxs-lookup"><span data-stu-id="efe6b-146">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="efe6b-147">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-147">If not found, fails.</span></span> <br><br> <span data-ttu-id="efe6b-148">Bu değer, SDK 'nın önceki sürümlerindeki eski davranıştır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-148">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="efe6b-149">Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-149">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="efe6b-150">Bulunamazsa, aynı birincil/ikincil içindeki bir sonraki yüksek Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-150">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="efe6b-151">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-151">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="efe6b-152">Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-152">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="efe6b-153">Bulunamazsa, aynı birincil/alt sürüm içindeki bir sonraki daha yüksek Özellik bandına kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-153">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="efe6b-154">Bulunamazsa, aynı ana sırada bir sonraki yüksek ve daha düşük Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-154">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="efe6b-155">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-155">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="efe6b-156">Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-156">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="efe6b-157">Bulunamazsa, aynı birincil/alt sürüm içindeki bir sonraki daha yüksek Özellik bandına kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-157">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="efe6b-158">Bulunamazsa, aynı ana sırada bir sonraki yüksek ve daha düşük Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-158">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="efe6b-159">Bulunamazsa, daha yüksek büyük, küçük ve özellik bandına ileri doğru kaydeder ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-159">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="efe6b-160">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-160">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="efe6b-161">, İstenen ana, alt ve özellik bandı ile bir düzeltme eki düzeyi ve belirtilen değerden daha büyük veya eşit olan en son yüklenen düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-161">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="efe6b-162">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-162">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="efe6b-163">, Belirtilen değerden daha büyük veya eşit olan bir özellik bandı ve düzeltme eki düzeyiyle istenen büyük ve küçük ile eşleşen en yüksek yüklü Özellik bandı ve düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-163">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="efe6b-164">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-164">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="efe6b-165">, Belirtilen değerden daha büyük veya eşit olan bir ikincil, özellik bandı ve yama düzeyiyle istenen ana, özellik bandı ve düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-165">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor, feature band, and patch level that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="efe6b-166">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-166">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="efe6b-167">En yüksek yüklü .NET Core SDK, belirtilen değerden daha büyük veya eşit olan bir sürümle kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-167">Uses the highest installed .NET Core SDK with a version that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="efe6b-168">Bulunamazsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-168">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="efe6b-169">İleri doğru değil.</span><span class="sxs-lookup"><span data-stu-id="efe6b-169">Doesn't roll forward.</span></span> <span data-ttu-id="efe6b-170">Tam eşleşme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-170">Exact match required.</span></span> |

### <a name="msbuild-sdks"></a><span data-ttu-id="efe6b-171">MSBuild-SDK 'lar</span><span class="sxs-lookup"><span data-stu-id="efe6b-171">msbuild-sdks</span></span>

<span data-ttu-id="efe6b-172">Türüyle `object`</span><span class="sxs-lookup"><span data-stu-id="efe6b-172">Type: `object`</span></span>

<span data-ttu-id="efe6b-173">Proje SDK sürümünü her bir proje yerine tek bir yerde denetlemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-173">Lets you control the project SDK version in one place rather than in each individual project.</span></span> <span data-ttu-id="efe6b-174">Daha fazla bilgi için bkz. [Proje SDK 'Ları nasıl çözümlenir](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span><span class="sxs-lookup"><span data-stu-id="efe6b-174">For more information, see [How project SDKs are resolved](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved).</span></span>

## <a name="examples"></a><span data-ttu-id="efe6b-175">Örnekler</span><span class="sxs-lookup"><span data-stu-id="efe6b-175">Examples</span></span>

<span data-ttu-id="efe6b-176">Aşağıdaki örnek, ön sürüm sürümlerinin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="efe6b-176">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="efe6b-177">Aşağıdaki örnek, belirtilen sürümden daha büyük veya eşit olan en yüksek sürümü nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-177">The following example shows how to use the highest version installed that is greater or equal than the specified version.</span></span> <span data-ttu-id="efe6b-178">Gösterilen JSON, 2.2.200 ' den önceki SDK sürümlerine izin vermez ve 3.0.xxx ve 3.1.xxx dahil olmak üzere 2.2.200 veya sonraki bir sürüme izin verir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-178">The JSON shown disallows any SDK version earlier than 2.2.200 and allows 2.2.200 or any later version, including 3.0.xxx and 3.1.xxx.</span></span>

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="efe6b-179">Aşağıdaki örnek, belirtilen sürümün tam olarak nasıl kullanılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="efe6b-179">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="efe6b-180">Aşağıdaki örnek, belirli bir büyük ve küçük sürümünün yüklü olduğu en son özellik bandı ve düzeltme eki sürümünü nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-180">The following example shows how to use the latest feature band and patch version installed of a specific major and minor version.</span></span> <span data-ttu-id="efe6b-181">Gösterilen JSON, 3.1.102 ' den önceki SDK sürümlerine izin vermez ve 3.1.102 ya da 3.1.103 veya 3.1.200 gibi daha sonraki 3.1.xxx sürümlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="efe6b-181">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.xxx version, such as 3.1.103 or 3.1.200.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

<span data-ttu-id="efe6b-182">Aşağıdaki örnek, belirli bir sürümün yüklü olduğu en yüksek düzeltme eki sürümünü nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-182">The following example shows how to use the highest patch version installed of a specific version.</span></span> <span data-ttu-id="efe6b-183">Gösterilen JSON, 3.1.102 ' den önceki SDK sürümlerine izin vermez ve 3.1.102 ya da 3.1.103 veya 3.1.199 gibi sonraki 3.1.1 xx sürümüne izin verir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-183">The JSON shown disallows any SDK version earlier than 3.1.102 and allows 3.1.102 or any later 3.1.1xx version, such as 3.1.103 or 3.1.199.</span></span>

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="efe6b-184">global.jsve .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="efe6b-184">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="efe6b-185">Dosyasında *global.js* bir tane ayarlamak için MAKINENIZDE hangi SDK sürümlerinin yüklü olduğunu bilmemiz yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-185">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="efe6b-186">Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [.NET Core 'un zaten yüklü olduğunu denetleme](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="efe6b-186">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="efe6b-187">Makinenize ek .NET Core SDK sürümleri yüklemek için [.NET Core 'U indir](https://dotnet.microsoft.com/download/dotnet-core) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="efe6b-187">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="efe6b-188">Aşağıdaki örneğe benzer şekilde, [DotNet New](dotnet-new.md) komutunu yürüterek geçerli dizinde dosya üzerinde yeni bir *global.js* oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="efe6b-188">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="efe6b-189">Eşleşen kurallar</span><span class="sxs-lookup"><span data-stu-id="efe6b-189">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="efe6b-190">Eşleşen kurallar `dotnet.exe` , tüm yüklü .net çekirdeği yüklü çalışma zamanları genelinde ortak olan giriş noktasına tabidir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-190">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="efe6b-191">.NET Core çalışma zamanının en son yüklü sürümü için eşleşen kurallar, yan yana birden fazla çalışma zamanı yüklediğinizde veya bir *global.js* dosya kullanıyorsanız kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-191">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side or if or you're using a *global.json* file.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="efe6b-192">.NET Core 3. x</span><span class="sxs-lookup"><span data-stu-id="efe6b-192">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="efe6b-193">.NET Core 3,0 ile başlayarak, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="efe6b-193">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="efe6b-194">Dosya *üzerindeglobal.js* bulunamazsa veya *global.js* bir SDK sürümü ya da bir değer belirtmezse `allowPrerelease` , en yüksek yüklü SDK sürümü kullanılır (ayarına eşdeğerdir `rollForward` `latestMajor` ).</span><span class="sxs-lookup"><span data-stu-id="efe6b-194">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="efe6b-195">Ön sürüm SDK sürümlerinin kabul edilip edilmediği, nasıl `dotnet` çağrıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-195">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="efe6b-196">Visual Studio 'da **değilseniz** , ön sürüm sürümleri göz önünde bulundurulmaz.</span><span class="sxs-lookup"><span data-stu-id="efe6b-196">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="efe6b-197">Visual Studio 'da çalışıyorsanız, istenen ön sürüm durumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-197">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="efe6b-198">Diğer bir deyişle, Visual Studio 'nun önizleme sürümünü kullanıyorsanız veya .NET Core SDK seçeneğinin ( **Araçlar** **Use previews of the .NET Core SDK**  >  **Seçenekler**  >  **ortamı**  >  **Önizleme özellikleri** altında) kullanım önizlemelerini ayarlarsanız, ön sürüm sürümlerinin kabul edilmesi gerekir; Aksi takdirde yalnızca yayın sürümleri kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-198">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features** ), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="efe6b-199">Bir SDK sürümü belirtmeyen, ancak bir değeri belirten bir *global.js* dosya bulunursa `allowPrerelease` , en yüksek yüklü SDK sürümü kullanılır (ayarına eşdeğerdir `rollForward` `latestMajor` ).</span><span class="sxs-lookup"><span data-stu-id="efe6b-199">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="efe6b-200">En son SDK sürümünün yayınlanıp yayınlanamayacağını veya ön sürümün değerine bağlı olup olmadığı `allowPrerelease` .</span><span class="sxs-lookup"><span data-stu-id="efe6b-200">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="efe6b-201">`true` ön sürüm sürümlerinin kabul edileceğini belirtir; `false` yalnızca yayın sürümlerinin kabul edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-201">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="efe6b-202">Dosyadaki bir *global.js* bulunursa ve bir SDK sürümü belirtiyorsa:</span><span class="sxs-lookup"><span data-stu-id="efe6b-202">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="efe6b-203">`rollForward`Değer ayarlanmamışsa, `latestPatch` varsayılan ilke olarak kullanır `rollForward` .</span><span class="sxs-lookup"><span data-stu-id="efe6b-203">If no `rollForward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="efe6b-204">Aksi takdirde, her bir değeri ve bunların davranışını [rollforward](#rollforward) bölümünde denetleyin.</span><span class="sxs-lookup"><span data-stu-id="efe6b-204">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="efe6b-205">Ön sürüm sürümlerinin göz önünde bulundurulmayacağı ve `allowPrerelease` ayarlanmadı ayarı, [Allowbir ön sürümü](#allowprerelease) bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-205">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="efe6b-206">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="efe6b-206">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="efe6b-207">.NET Core 2. x SDK 'da, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="efe6b-207">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="efe6b-208">Dosya *üzerindeglobal.js* bulunamazsa veya *global.jsüzerinde* bir SDK sürümü belirtilmemişse, en son yüklenen SDK sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-208">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="efe6b-209">En son SDK sürümü yayın veya ön sürüm olabilir; en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-209">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="efe6b-210">*global.json* bir SDK sürümü belirtirseniz:</span><span class="sxs-lookup"><span data-stu-id="efe6b-210">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="efe6b-211">Makinede belirtilen SDK sürümü bulunursa, bu tam sürüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-211">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="efe6b-212">Makinede belirtilen SDK sürümü bulunamazsa, bu sürümün en son yüklenen SDK **düzeltme eki sürümü** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-212">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="efe6b-213">En son yüklenen SDK **düzeltme eki sürümü** sürüm veya ön sürüm olabilir; en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-213">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="efe6b-214">.NET Core 2,1 ve üzeri sürümlerde, belirtilen **Düzeltme Eki sürümünden** düşük olan **yama sürümleri** SDK seçiminde yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-214">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="efe6b-215">Belirtilen SDK sürümü ve uygun bir SDK **yaması sürümü** bulunamazsa hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="efe6b-215">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="efe6b-216">SDK sürümü aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="efe6b-216">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="efe6b-217">.NET Core SDK **özellik sürümü** , `x` `xyz` SDK sürümleri 2.1.100 ve üzeri için () sayının son parçasında () ilk basamak () ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-217">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="efe6b-218">Genel olarak, .NET Core SDK .NET Core 'dan daha hızlı bir yayın döngüsüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-218">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="efe6b-219">**Düzeltme eki sürümü** , `yz` `xyz` SDK sürümleri 2.1.100 ve üzeri için () sayısının son bölümünde son iki basamak () tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-219">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="efe6b-220">Örneğin, `2.1.300` SDK sürümü olarak belirtirseniz, SDK seçimi için en fazla bulur `2.1.399` ancak `2.1.400` için bir düzeltme eki sürümü kabul edilmez `2.1.300` .</span><span class="sxs-lookup"><span data-stu-id="efe6b-220">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="efe6b-221">Aracılığıyla .NET Core SDK `2.1.100` sürümler `2.1.201` sürüm numarası şemaları arasındaki geçiş sırasında yayımlanmıştır ve gösterimi doğru şekilde işlemez `xyz` .</span><span class="sxs-lookup"><span data-stu-id="efe6b-221">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="efe6b-222">Bu sürümleri dosyada *global.js* belirtirseniz, belirtilen sürümlerin hedef makinelerde olduğundan emin olmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-222">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="efe6b-223">Derleme uyarıları sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="efe6b-223">Troubleshoot build warnings</span></span>

* <span data-ttu-id="efe6b-224">Aşağıdaki uyarı, projenizin .NET Core SDK ön sürümü kullanılarak derlendiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="efe6b-224">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="efe6b-225">.NET Core SDK bir önizleme sürümü ile çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="efe6b-225">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="efe6b-226">SDK sürümünü geçerli projedeki bir global.jsile tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efe6b-226">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="efe6b-227">Daha fazlası <https://go.microsoft.com/fwlink/?linkid=869452> :</span><span class="sxs-lookup"><span data-stu-id="efe6b-227">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="efe6b-228">.NET Core SDK sürümlerde yüksek kaliteli bir geçmiş ve taahhüt vardır.</span><span class="sxs-lookup"><span data-stu-id="efe6b-228">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="efe6b-229">Ancak, bir ön sürüm sürümü kullanmak istemiyorsanız, .NET Core 3,0 SDK ile kullanabileceğiniz farklı stratejileri veya [allowbir ön](#allowprerelease) sürümü bölümünde daha sonraki bir sürümü kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="efe6b-229">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="efe6b-230">.NET Core 3,0 veya daha yüksek bir çalışma zamanı veya SDK yüklü olmayan makinelerde, dosya *üzerinde birglobal.js* oluşturmanız ve kullanmak istediğiniz tam sürümü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-230">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="efe6b-231">Aşağıdaki uyarı, projenizin .NET Core 2,1 SDK ve sonraki sürümlerle uyumlu olmayan 1,0 veya 1,1 EF Core hedeflediği anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="efe6b-231">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="efe6b-232">' {StartupProject} ' başlangıç projesi Framework 'ü hedefliyor. NETCoreApp ' sürümü ' {targetFrameworkVersion} '.</span><span class="sxs-lookup"><span data-stu-id="efe6b-232">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="efe6b-233">Entity Framework Core .NET komut satırı araçlarının bu sürümü yalnızca sürüm 2,0 veya üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="efe6b-233">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="efe6b-234">Araçların eski sürümlerini kullanma hakkında daha fazla bilgi için bkz <https://go.microsoft.com/fwlink/?linkid=871254> ..</span><span class="sxs-lookup"><span data-stu-id="efe6b-234">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="efe6b-235">.NET Core 2,1 SDK (sürüm 2.1.300) ile başlayarak, `dotnet ef` komut SDK 'ya dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="efe6b-235">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="efe6b-236">Projenizi derlemek için, makinenizde .NET Core 2,0 SDK (sürüm 2.1.201) veya daha önceki bir sürümünü yükledikten sonra *global.json* dosya kullanarak istenen SDK sürümünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="efe6b-236">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="efe6b-237">Komutu hakkında daha fazla bilgi için `dotnet ef` bkz. [.NET komut satırı araçlarını EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="efe6b-237">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="efe6b-238">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efe6b-238">See also</span></span>

- [<span data-ttu-id="efe6b-239">Proje SDK 'Ları nasıl çözümlenir</span><span class="sxs-lookup"><span data-stu-id="efe6b-239">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)

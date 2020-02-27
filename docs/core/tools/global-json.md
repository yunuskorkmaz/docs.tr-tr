---
title: global.json’a genel bakış
description: .NET Core CLI komutlarını çalıştırırken .NET Core SDK sürümünü ayarlamak için Global. json dosyasını nasıl kullanacağınızı öğrenin.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 70257566e1ff30f5c97212a5e0e3c308c27738b7
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626001"
---
# <a name="globaljson-overview"></a><span data-ttu-id="377d5-103">global.json’a genel bakış</span><span class="sxs-lookup"><span data-stu-id="377d5-103">global.json overview</span></span>

<span data-ttu-id="377d5-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="377d5-104">**This article applies to:** ✔️ .NET Core 2.0 SDK and later versions</span></span>

<span data-ttu-id="377d5-105">*Global. JSON* dosyası, .NET Core CLI komutlarını çalıştırdığınızda hangi .NET Core SDK sürümünün kullanıldığını tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="377d5-105">The *global.json* file allows you to define which .NET Core SDK version is used when you run .NET Core CLI commands.</span></span> <span data-ttu-id="377d5-106">.NET Core SDK seçilmesi, projenizin hedeflediği çalışma zamanını belirtmekten bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="377d5-106">Selecting the .NET Core SDK is independent from specifying the runtime your project targets.</span></span> <span data-ttu-id="377d5-107">.NET Core SDK sürümü .NET Core CLI hangi sürümlerinin kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="377d5-107">The .NET Core SDK version indicates which versions of the .NET Core CLI is used.</span></span>

<span data-ttu-id="377d5-108">Genel olarak, SDK araçlarının en son sürümünü kullanmak istiyorsunuz, bu nedenle *Global. JSON* dosyası gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="377d5-108">In general, you want to use the latest version of the SDK tools, so no *global.json* file is needed.</span></span> <span data-ttu-id="377d5-109">Bazı Gelişmiş senaryolarda, SDK araçlarının sürümünü denetlemek isteyebilirsiniz ve bu makalede bunun nasıl yapılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-109">In some advanced scenarios, you might want to control the version of the SDK tools, and this article explains how to do this.</span></span>

<span data-ttu-id="377d5-110">Bunun yerine çalışma zamanının belirtilmesi hakkında daha fazla bilgi için bkz. [hedef çerçeveler](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="377d5-110">For more information about specifying the runtime instead, see [Target frameworks](../../standard/frameworks.md).</span></span>

<span data-ttu-id="377d5-111">.NET Core SDK geçerli çalışma dizininde (proje diziniyle aynı olmayan) veya üst dizinlerinden biri olan *Global. JSON* dosyasını arar.</span><span class="sxs-lookup"><span data-stu-id="377d5-111">.NET Core SDK looks for a *global.json* file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="globaljson-schema"></a><span data-ttu-id="377d5-112">Global. JSON şeması</span><span class="sxs-lookup"><span data-stu-id="377d5-112">global.json schema</span></span>

### <a name="sdk"></a><span data-ttu-id="377d5-113">sdk</span><span class="sxs-lookup"><span data-stu-id="377d5-113">sdk</span></span>

<span data-ttu-id="377d5-114">Tür: `object`</span><span class="sxs-lookup"><span data-stu-id="377d5-114">Type: `object`</span></span>

<span data-ttu-id="377d5-115">Seçilecek .NET Core SDK hakkındaki bilgileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="377d5-115">Specifies information about the .NET Core SDK to select.</span></span>

#### <a name="version"></a><span data-ttu-id="377d5-116">version</span><span class="sxs-lookup"><span data-stu-id="377d5-116">version</span></span>

- <span data-ttu-id="377d5-117">Tür: `string`</span><span class="sxs-lookup"><span data-stu-id="377d5-117">Type: `string`</span></span>

- <span data-ttu-id="377d5-118">Şu tarihten itibaren kullanılabilir: .NET Core 1,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="377d5-118">Available since: .NET Core 1.0 SDK.</span></span>

<span data-ttu-id="377d5-119">Kullanılacak .NET Core SDK sürümü.</span><span class="sxs-lookup"><span data-stu-id="377d5-119">The version of the .NET Core SDK to use.</span></span>

<span data-ttu-id="377d5-120">Bu alan:</span><span class="sxs-lookup"><span data-stu-id="377d5-120">This field:</span></span>

- <span data-ttu-id="377d5-121">Joker karakter desteği yoktur, yani tam sürüm numarası belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="377d5-121">Doesn't have wildcard support, that is, the full version number has to be specified.</span></span>
- <span data-ttu-id="377d5-122">Sürüm aralıklarını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="377d5-122">Doesn't support version ranges.</span></span>

#### <a name="allowprerelease"></a><span data-ttu-id="377d5-123">Allowönsürümü</span><span class="sxs-lookup"><span data-stu-id="377d5-123">allowPrerelease</span></span>

- <span data-ttu-id="377d5-124">Tür: `boolean`</span><span class="sxs-lookup"><span data-stu-id="377d5-124">Type: `boolean`</span></span>

- <span data-ttu-id="377d5-125">Şu tarihten itibaren kullanılabilir: .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="377d5-125">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="377d5-126">SDK Çözümleyicisinin kullanılacak SDK sürümünü seçerken yayın öncesi sürümlerini düşünmesinin gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="377d5-126">Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>

<span data-ttu-id="377d5-127">Bu değeri açıkça ayarlamazsanız, varsayılan değer Visual Studio 'dan çalıştırıp çalıştırdığınıza bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="377d5-127">If you don't set this value explicitly, the default value depends on whether you're running from Visual Studio:</span></span>

- <span data-ttu-id="377d5-128">Visual Studio 'da **değilseniz** , varsayılan değer `true`olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-128">If you're **not** in Visual Studio, the default value is `true`.</span></span>
- <span data-ttu-id="377d5-129">Visual Studio 'da çalışıyorsanız, istenen ön sürüm durumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-129">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="377d5-130">Diğer bir deyişle, Visual Studio 'nun bir önizleme sürümünü kullanıyorsanız veya .NET Core SDK seçeneğinin ( **araçlar** > **seçenekler** > **ortam** > **Önizleme özellikleri**) **kullanım önizlemelerini** ayarlarsanız, varsayılan değer `true`olur; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="377d5-130">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), the default value is `true`; otherwise, `false`.</span></span>

#### <a name="rollforward"></a><span data-ttu-id="377d5-131">Ileri alınmaya</span><span class="sxs-lookup"><span data-stu-id="377d5-131">rollForward</span></span>

- <span data-ttu-id="377d5-132">Tür: `string`</span><span class="sxs-lookup"><span data-stu-id="377d5-132">Type: `string`</span></span>

- <span data-ttu-id="377d5-133">Şu tarihten itibaren kullanılabilir: .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="377d5-133">Available since: .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="377d5-134">Bir SDK sürümü seçerken kullanılacak geri alma ilkesi, belirli bir SDK sürümü eksik olduğunda geri dönüş olarak veya daha yüksek bir sürümü kullanmak için bir yönerge olarak.</span><span class="sxs-lookup"><span data-stu-id="377d5-134">The roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span> <span data-ttu-id="377d5-135">Bir [Sürüm](#version) , `latestMajor`ayarmadığınız müddetçe `rollForward` değerle belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="377d5-135">A [version](#version) must be specified with a `rollForward` value, unless you're setting it to `latestMajor`.</span></span>

<span data-ttu-id="377d5-136">Kullanılabilir ilkeleri ve bunların davranışlarını anlamak için `x.y.znn`biçimdeki SDK sürümü için aşağıdaki tanımları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="377d5-136">To understand the available policies and their behavior, consider the following definitions for an SDK version in the format `x.y.znn`:</span></span>

- <span data-ttu-id="377d5-137">ana sürümdür `x`.</span><span class="sxs-lookup"><span data-stu-id="377d5-137">`x` is the major version.</span></span>
- <span data-ttu-id="377d5-138">`y`, ikincil sürümdür.</span><span class="sxs-lookup"><span data-stu-id="377d5-138">`y` is the minor version.</span></span>
- <span data-ttu-id="377d5-139">`z`, özellik bantdır.</span><span class="sxs-lookup"><span data-stu-id="377d5-139">`z` is the feature band.</span></span>
- <span data-ttu-id="377d5-140">`nn` düzeltme eki sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="377d5-140">`nn` is the patch version.</span></span>

<span data-ttu-id="377d5-141">Aşağıdaki tabloda `rollForward` anahtarı için olası değerler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="377d5-141">The following table shows the possible values for the `rollForward` key:</span></span>

| <span data-ttu-id="377d5-142">Değer</span><span class="sxs-lookup"><span data-stu-id="377d5-142">Value</span></span>         | <span data-ttu-id="377d5-143">Davranış</span><span class="sxs-lookup"><span data-stu-id="377d5-143">Behavior</span></span> |
| ------------- | ---------- |
| `patch`       | <span data-ttu-id="377d5-144">Belirtilen sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-144">Uses the specified version.</span></span> <br> <span data-ttu-id="377d5-145">Bulunamazsa, en son düzeltme eki düzeyine doğru kaydeder.</span><span class="sxs-lookup"><span data-stu-id="377d5-145">If not found, rolls forward to the latest patch level.</span></span> <br> <span data-ttu-id="377d5-146">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-146">If not found, fails.</span></span> <br><br> <span data-ttu-id="377d5-147">Bu değer, SDK 'nın önceki sürümlerindeki eski davranıştır.</span><span class="sxs-lookup"><span data-stu-id="377d5-147">This value is the legacy behavior from the earlier versions of the SDK.</span></span> |
| `feature`     | <span data-ttu-id="377d5-148">Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-148">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="377d5-149">Bulunamazsa, aynı birincil/ikincil içindeki bir sonraki yüksek Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-149">If not found, rolls forward to the next higher feature band within the same major/minor and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="377d5-150">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-150">If not found, fails.</span></span> |
| `minor`       | <span data-ttu-id="377d5-151">Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-151">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="377d5-152">Bulunamazsa, aynı birincil/alt sürüm içindeki bir sonraki daha yüksek Özellik bandına kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-152">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="377d5-153">Bulunamazsa, aynı ana sırada bir sonraki yüksek ve daha düşük Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-153">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="377d5-154">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-154">If not found, fails.</span></span> |
| `major`       | <span data-ttu-id="377d5-155">Belirtilen ana, ikincil ve özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-155">Uses the latest patch level for the specified major, minor, and feature band.</span></span> <br> <span data-ttu-id="377d5-156">Bulunamazsa, aynı birincil/alt sürüm içindeki bir sonraki daha yüksek Özellik bandına kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-156">If not found, rolls forward to the next higher feature band within the same major/minor version and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="377d5-157">Bulunamazsa, aynı ana sırada bir sonraki yüksek ve daha düşük Özellik bandına doğru kaydolur ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-157">If not found, rolls forward to the next higher minor and feature band within the same major and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="377d5-158">Bulunamazsa, daha yüksek büyük, küçük ve özellik bandına ileri doğru kaydeder ve bu özellik bandı için en son düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-158">If not found, rolls forward to the next higher major, minor, and feature band and uses the latest patch level for that feature band.</span></span> <br> <span data-ttu-id="377d5-159">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-159">If not found, fails.</span></span> |
| `latestPatch` | <span data-ttu-id="377d5-160">, İstenen ana, alt ve özellik bandı ile bir düzeltme eki düzeyi ve belirtilen değerden daha büyük veya eşit olan en son yüklenen düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-160">Uses the latest installed patch level that matches the requested major, minor, and feature band with a patch level and that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="377d5-161">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-161">If not found, fails.</span></span> |
| `latestFeature` | <span data-ttu-id="377d5-162">, Belirtilen değerden daha büyük veya eşit olan bir özellik bandı ile istenen büyük ve küçük ile eşleşen en yüksek yüklü Özellik bandı ve düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-162">Uses the highest installed feature band and patch level that matches the requested major and minor with a feature band that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="377d5-163">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-163">If not found, fails.</span></span> |
| `latestMinor` | <span data-ttu-id="377d5-164">, Belirtilen değerden daha büyük veya ona eşit olan, istenen ana ile eşleşen en yüksek alt, özellik bandı ve düzeltme eki düzeyini kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-164">Uses the highest installed minor, feature band, and patch level that matches the requested major with a minor that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="377d5-165">Bulunamazsa, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-165">If not found, fails.</span></span> |
| `latestMajor` | <span data-ttu-id="377d5-166">, Belirtilen değerden büyük veya eşit olan en yüksek yüklü .NET Core SDK kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-166">Uses the highest installed .NET Core SDK with a major that is greater or equal than the specified value.</span></span> <br> <span data-ttu-id="377d5-167">Bulunamazsa başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-167">If not found, fail.</span></span> |
| `disable`     | <span data-ttu-id="377d5-168">İleri doğru değil.</span><span class="sxs-lookup"><span data-stu-id="377d5-168">Doesn't roll forward.</span></span> <span data-ttu-id="377d5-169">Tam eşleşme gereklidir.</span><span class="sxs-lookup"><span data-stu-id="377d5-169">Exact match required.</span></span> |

## <a name="examples"></a><span data-ttu-id="377d5-170">Örnekler</span><span class="sxs-lookup"><span data-stu-id="377d5-170">Examples</span></span>

<span data-ttu-id="377d5-171">Aşağıdaki örnek, ön sürüm sürümlerinin nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="377d5-171">The following example shows how to not use prerelease versions:</span></span>

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

<span data-ttu-id="377d5-172">Aşağıdaki örnek, belirtilen sürümden daha büyük veya eşit olan en yüksek sürümü nasıl kullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="377d5-172">The following example shows how to use the highest version installed that is greater or equal than the specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

<span data-ttu-id="377d5-173">Aşağıdaki örnek, belirtilen sürümün tam olarak nasıl kullanılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="377d5-173">The following example shows how to use the exact specified version:</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

<span data-ttu-id="377d5-174">Aşağıdaki örnek, belirli bir sürümün yüklü olduğu en yüksek düzeltme eki sürümünün (3.1.1 xx biçiminde) nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="377d5-174">The following example shows how to use the highest patch version installed of a specific version (in the form, 3.1.1xx):</span></span>

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a><span data-ttu-id="377d5-175">Global. JSON ve .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="377d5-175">global.json and the .NET Core CLI</span></span>

<span data-ttu-id="377d5-176">*Global. JSON* dosyasında bir tane ayarlamak için MAKINENIZDE hangi SDK sürümlerinin yüklü olduğunu bilmemiz yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="377d5-176">It's helpful to know which SDK versions are installed on your machine to set one in the *global.json* file.</span></span> <span data-ttu-id="377d5-177">Bunun nasıl yapılacağı hakkında daha fazla bilgi için bkz. [.NET Core 'un zaten yüklü olduğunu denetleme](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span><span class="sxs-lookup"><span data-stu-id="377d5-177">For more information on how to do that, see [How to check that .NET Core is already installed](../install/how-to-detect-installed-versions.md#check-sdk-versions).</span></span>

<span data-ttu-id="377d5-178">Makinenize ek .NET Core SDK sürümleri yüklemek için [.NET Core 'U indir](https://dotnet.microsoft.com/download/dotnet-core) sayfasını ziyaret edin.</span><span class="sxs-lookup"><span data-stu-id="377d5-178">To install additional .NET Core SDK versions on your machine, visit the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>

<span data-ttu-id="377d5-179">Aşağıdaki örneğe benzer şekilde, [DotNet New](dotnet-new.md) komutunu yürüterek geçerli dizinde yeni bir *Global. JSON* dosyası oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="377d5-179">You can create a new the *global.json* file in the current directory by executing the [dotnet new](dotnet-new.md) command, similar to the following example:</span></span>

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a><span data-ttu-id="377d5-180">Eşleşen kurallar</span><span class="sxs-lookup"><span data-stu-id="377d5-180">Matching rules</span></span>

> [!NOTE]
> <span data-ttu-id="377d5-181">Eşleşen kurallar, yüklü olan tüm .NET çekirdeği yüklü çalışma zamanları genelinde ortak olan `dotnet.exe` giriş noktasına tabidir.</span><span class="sxs-lookup"><span data-stu-id="377d5-181">The matching rules are governed by the `dotnet.exe` entry point, which is common across all installed .NET Core installed runtimes.</span></span> <span data-ttu-id="377d5-182">.NET Core çalışma zamanının en son yüklü sürümü için eşleşen kurallar, yan yana birden çok çalışma zamanı yüklendiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="377d5-182">The matching rules for the latest installed version of the .NET Core Runtime are used when you have multiple runtimes installed side-by-side.</span></span>

## <a name="net-core-3x"></a>[<span data-ttu-id="377d5-183">.NET Core 3. x</span><span class="sxs-lookup"><span data-stu-id="377d5-183">.NET Core 3.x</span></span>](#tab/netcore3x)

<span data-ttu-id="377d5-184">.NET Core 3,0 ile başlayarak, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="377d5-184">Starting with .NET Core 3.0, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="377d5-185">Global. *JSON* dosyası bulunmazsa veya *Global. JSON* bir SDK sürümü veya bir `allowPrerelease` değeri belirtmezse, en yüksek yüklü SDK sürümü kullanılır (`rollForward` ayarı `latestMajor`olarak eşdeğerdir).</span><span class="sxs-lookup"><span data-stu-id="377d5-185">If no *global.json* file is found, or *global.json* doesn't specify an SDK version nor an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="377d5-186">Ön sürüm SDK sürümlerinin kabul edilip edilmediği, `dotnet` nasıl çağrıldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="377d5-186">Whether prerelease SDK versions are considered depends on how `dotnet` is being invoked.</span></span>
  - <span data-ttu-id="377d5-187">Visual Studio 'da **değilseniz** , ön sürüm sürümleri göz önünde bulundurulmaz.</span><span class="sxs-lookup"><span data-stu-id="377d5-187">If you're **not** in Visual Studio, prerelease versions are considered.</span></span>
  - <span data-ttu-id="377d5-188">Visual Studio 'da çalışıyorsanız, istenen ön sürüm durumunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-188">If you are in Visual Studio, it uses the prerelease status requested.</span></span> <span data-ttu-id="377d5-189">Diğer bir deyişle, Visual Studio 'nun önizleme sürümünü kullanıyorsanız veya .NET Core SDK seçeneğinin ( **araçlar** > **seçenekler** > **ortam** > **Önizleme özellikleri**) **kullanım önizlemelerini** ayarlarsanız, ön sürüm sürümleri göz önünde bulundurululur; Aksi takdirde, yalnızca yayın sürümleri kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="377d5-189">That is, if you're using a Preview version of Visual Studio or you set the **Use previews of the .NET Core SDK** option (under **Tools** > **Options** > **Environment** > **Preview Features**), prerelease versions are considered; otherwise, only release versions are considered.</span></span>
- <span data-ttu-id="377d5-190">Bir SDK sürümü belirtmeyen, ancak bir `allowPrerelease` değerini belirten bir *Global. JSON* dosyası bulunursa, en yüksek yüklü SDK sürümü kullanılır (`latestMajor``rollForward` ayarlamaya eşdeğerdir).</span><span class="sxs-lookup"><span data-stu-id="377d5-190">If a *global.json* file is found that doesn't specify an SDK version but it specifies an `allowPrerelease` value, the highest installed SDK version is used (equivalent to setting `rollForward` to `latestMajor`).</span></span> <span data-ttu-id="377d5-191">En son SDK sürümünün yayınlanıp yayınlanamayacağını veya ön sürümü `allowPrerelease`değerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="377d5-191">Whether the latest SDK version can be release or prerelease depends on the value of `allowPrerelease`.</span></span> <span data-ttu-id="377d5-192">`true`, ön sürüm sürümlerinin kabul edileceğini belirtir; `false` yalnızca yayın sürümlerinin kabul edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="377d5-192">`true` indicates prerelease versions are considered; `false` indicates that only release versions are considered.</span></span>
- <span data-ttu-id="377d5-193">Bir *Global. JSON* dosyası bulunursa ve bir SDK sürümü belirtiyorsa:</span><span class="sxs-lookup"><span data-stu-id="377d5-193">If a *global.json* file is found and it specifies an SDK version:</span></span>

  - <span data-ttu-id="377d5-194">`rollFoward` değer ayarlanmamışsa, varsayılan `rollForward` ilkesi olarak `latestPatch` kullanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-194">If no `rollFoward` value is set, it uses `latestPatch` as the default `rollForward` policy.</span></span> <span data-ttu-id="377d5-195">Aksi takdirde, her bir değeri ve bunların davranışını [rollforward](#rollforward) bölümünde denetleyin.</span><span class="sxs-lookup"><span data-stu-id="377d5-195">Otherwise, check each value and their behavior in the [rollForward](#rollforward) section.</span></span>
  - <span data-ttu-id="377d5-196">Ön sürüm sürümlerinin dikkate alınıp alınmayacağını ve `allowPrerelease` ayarlanmamışsa, [Allowbir ön sürümü](#allowprerelease) bölümünde açıklanan varsayılan davranış nedir?</span><span class="sxs-lookup"><span data-stu-id="377d5-196">Whether prerelease versions are considered and what's the default behavior when `allowPrerelease` isn't set is described in the [allowPrerelease](#allowprerelease) section.</span></span>

## <a name="net-core-2x"></a>[<span data-ttu-id="377d5-197">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="377d5-197">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="377d5-198">.NET Core 2. x SDK 'da, hangi SDK sürümünün kullanılacağını belirlerken aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="377d5-198">In .NET Core 2.x SDK, the following rules apply when determining which version of the SDK to use:</span></span>

- <span data-ttu-id="377d5-199">*Global. JSON* dosyası bulunmazsa veya *geneldir. JSON* bir SDK sürümü belirtmez, en son yüklenen SDK sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="377d5-199">If no *global.json* file is found or *global.json* doesn't specify an SDK version, the latest installed SDK version is used.</span></span> <span data-ttu-id="377d5-200">En son SDK sürümü yayın veya ön sürüm olabilir; en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-200">Latest SDK version can be either release or prerelease - the highest version number wins.</span></span>
- <span data-ttu-id="377d5-201">*Global. JSON* bir SDK sürümü belirtirseniz:</span><span class="sxs-lookup"><span data-stu-id="377d5-201">If *global.json* does specify an SDK version:</span></span>
  - <span data-ttu-id="377d5-202">Makinede belirtilen SDK sürümü bulunursa, bu tam sürüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="377d5-202">If the specified SDK version is found on the machine, that exact version is used.</span></span>
  - <span data-ttu-id="377d5-203">Makinede belirtilen SDK sürümü bulunamazsa, bu sürümün en son yüklenen SDK **düzeltme eki sürümü** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="377d5-203">If the specified SDK version can't be found on the machine, the latest installed SDK **patch version** of that version is used.</span></span> <span data-ttu-id="377d5-204">En son yüklenen SDK **düzeltme eki sürümü** sürüm veya ön sürüm olabilir; en yüksek sürüm numarası kazanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-204">Latest installed SDK **patch version** can be either release or prerelease - the highest version number wins.</span></span> <span data-ttu-id="377d5-205">.NET Core 2,1 ve üzeri sürümlerde, belirtilen **Düzeltme Eki sürümünden** düşük olan **yama sürümleri** SDK seçiminde yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="377d5-205">In .NET Core 2.1 and higher, the **patch versions** lower than the **patch version** specified are ignored in the SDK selection.</span></span>
  - <span data-ttu-id="377d5-206">Belirtilen SDK sürümü ve uygun bir SDK **yaması sürümü** bulunamazsa hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="377d5-206">If the specified SDK version and an appropriate SDK **patch version** can't be found, an error is thrown.</span></span>

<span data-ttu-id="377d5-207">SDK sürümü aşağıdaki bölümlerden oluşur:</span><span class="sxs-lookup"><span data-stu-id="377d5-207">The SDK version is composed of the following parts:</span></span>

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

<span data-ttu-id="377d5-208">.NET Core SDK **özellik sürümü** , SDK sürümleri 2.1.100 ve üzeri için sayının (`xyz`) son parçasında ilk basamak (`x`) ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="377d5-208">The **feature release** of the .NET Core SDK is represented by the first digit (`x`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="377d5-209">Genel olarak, .NET Core SDK .NET Core 'dan daha hızlı bir yayın döngüsüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="377d5-209">In general, the .NET Core SDK has a faster release cycle than .NET Core.</span></span>

<span data-ttu-id="377d5-210">**Düzeltme eki sürümü** , SDK sürümleri 2.1.100 ve üzeri için sayının (`xyz`) son bölümünde son iki basamak (`yz`) tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="377d5-210">The **patch version** is defined by the last two digits (`yz`) in the last portion of the number (`xyz`) for SDK versions 2.1.100 and higher.</span></span> <span data-ttu-id="377d5-211">Örneğin, SDK sürümü olarak `2.1.300` belirtirseniz, SDK seçimi en fazla `2.1.399` bulur ancak `2.1.400` `2.1.300`için bir düzeltme eki sürümü olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="377d5-211">For example, if you specify `2.1.300` as the SDK version, SDK selection finds up to `2.1.399` but `2.1.400` isn't considered a patch version for `2.1.300`.</span></span>

<span data-ttu-id="377d5-212">`2.1.201` aracılığıyla `2.1.100` .NET Core SDK sürümler sürüm numarası şemaları arasındaki geçiş sırasında yayımlanmıştır ve `xyz` gösterimini doğru şekilde işlemez.</span><span class="sxs-lookup"><span data-stu-id="377d5-212">.NET Core SDK versions `2.1.100` through `2.1.201` were released during the transition between version number schemes and don't correctly handle the `xyz` notation.</span></span> <span data-ttu-id="377d5-213">Bu sürümleri *Global. JSON* dosyasında belirtirseniz, belirtilen sürümlerin hedef makinelerde olduğundan emin olmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="377d5-213">We highly recommend if you specify these versions in the *global.json* file, that you ensure the specified versions are on the target machines.</span></span>

---

## <a name="troubleshoot-build-warnings"></a><span data-ttu-id="377d5-214">Derleme uyarıları sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="377d5-214">Troubleshoot build warnings</span></span>

* <span data-ttu-id="377d5-215">Aşağıdaki uyarı, projenizin .NET Core SDK ön sürümü kullanılarak derlendiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="377d5-215">The following warning indicates that your project was compiled using a prerelease version of the .NET Core SDK:</span></span>

  > <span data-ttu-id="377d5-216">.NET Core SDK bir önizleme sürümü ile çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="377d5-216">You are working with a preview version of the .NET Core SDK.</span></span> <span data-ttu-id="377d5-217">SDK sürümünü geçerli projedeki Global. JSON dosyası aracılığıyla tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="377d5-217">You can define the SDK version via a global.json file in the current project.</span></span> <span data-ttu-id="377d5-218">Daha fazla <https://go.microsoft.com/fwlink/?linkid=869452>.</span><span class="sxs-lookup"><span data-stu-id="377d5-218">More at <https://go.microsoft.com/fwlink/?linkid=869452>.</span></span>

  <span data-ttu-id="377d5-219">.NET Core SDK sürümlerde yüksek kaliteli bir geçmiş ve taahhüt vardır.</span><span class="sxs-lookup"><span data-stu-id="377d5-219">.NET Core SDK versions have a history and commitment of being high quality.</span></span> <span data-ttu-id="377d5-220">Ancak, bir ön sürüm sürümü kullanmak istemiyorsanız, .NET Core 3,0 SDK ile kullanabileceğiniz farklı stratejileri veya [allowbir ön](#allowprerelease) sürümü bölümünde daha sonraki bir sürümü kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="377d5-220">However, if you don't want to use a prerelease version, check the different strategies you can use with the .NET Core 3.0 SDK or a later version in the [allowPrerelease](#allowprerelease) section.</span></span> <span data-ttu-id="377d5-221">.NET Core 3,0 veya daha yüksek bir çalışma zamanı veya SDK yüklü olmayan makinelerde, bir *Global. JSON* dosyası oluşturmanız ve kullanmak istediğiniz tam sürümü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="377d5-221">For machines that have never had a .NET Core 3.0 or higher Runtime or SDK installed, you need to create a *global.json* file and specify the exact version you want to use.</span></span>

* <span data-ttu-id="377d5-222">Aşağıdaki uyarı, projenizin .NET Core 2,1 SDK ve sonraki sürümlerle uyumlu olmayan 1,0 veya 1,1 EF Core hedeflediği anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="377d5-222">The following warning indicates that your project targets EF Core 1.0 or 1.1, which isn't compatible with .NET Core 2.1 SDK and later versions:</span></span>

  > <span data-ttu-id="377d5-223">' {StartupProject} ' başlangıç projesi Framework 'ü hedefliyor. NETCoreApp ' sürümü ' {targetFrameworkVersion} '.</span><span class="sxs-lookup"><span data-stu-id="377d5-223">Startup project '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'.</span></span> <span data-ttu-id="377d5-224">Entity Framework Core .NET komut satırı araçlarının bu sürümü yalnızca sürüm 2,0 veya üstünü destekler.</span><span class="sxs-lookup"><span data-stu-id="377d5-224">This version of the Entity Framework Core .NET Command-line Tools only supports version 2.0 or higher.</span></span> <span data-ttu-id="377d5-225">Araçların eski sürümlerini kullanma hakkında daha fazla bilgi için bkz. <https://go.microsoft.com/fwlink/?linkid=871254>.</span><span class="sxs-lookup"><span data-stu-id="377d5-225">For information on using older versions of the tools, see <https://go.microsoft.com/fwlink/?linkid=871254>.</span></span>

  <span data-ttu-id="377d5-226">.NET Core 2,1 SDK (sürüm 2.1.300) ile başlayarak, `dotnet ef` komutu SDK 'ya dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="377d5-226">Starting with .NET Core 2.1 SDK (version 2.1.300), the `dotnet ef` command comes included in the SDK.</span></span> <span data-ttu-id="377d5-227">Projenizi derlemek için, makinenizde .NET Core 2,0 SDK 'sını (sürüm 2.1.201) veya daha önceki bir sürümü yükleyip *Global. JSON* dosyasını kullanarak istenen SDK sürümünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="377d5-227">To compile your project, install .NET Core 2.0 SDK (version 2.1.201) or earlier on your machine and define the desired SDK version using the *global.json* file.</span></span> <span data-ttu-id="377d5-228">`dotnet ef` komutu hakkında daha fazla bilgi için bkz. [EF Core .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="377d5-228">For more information about the `dotnet ef` command, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

## <a name="see-also"></a><span data-ttu-id="377d5-229">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="377d5-229">See also</span></span>

- [<span data-ttu-id="377d5-230">Proje SDK 'Ları nasıl çözümlenir</span><span class="sxs-lookup"><span data-stu-id="377d5-230">How project SDKs are resolved</span></span>](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)

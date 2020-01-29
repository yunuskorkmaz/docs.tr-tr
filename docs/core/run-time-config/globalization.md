---
title: Genelleştirme yapılandırma ayarları
description: .NET Core uygulamasının Genelleştirme yönlerini yapılandıran çalışma zamanı ayarları hakkında bilgi edinin. Örneğin, Japonca tarihleri nasıl ayrıştırır.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733458"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="bfa14-103">Genelleştirme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="bfa14-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="bfa14-104">Sabit mod</span><span class="sxs-lookup"><span data-stu-id="bfa14-104">Invariant mode</span></span>

- <span data-ttu-id="bfa14-105">.NET Core uygulamasının kültüre özgü verilere ve davranışa erişim olmadan Genelleştirme sabit modunda çalışıp çalışmadığını ya da kültürel verilerine erişip erişemeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bfa14-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="bfa14-106">Varsayılan: uygulamayı, kültürel verileri (`false`) erişimi ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bfa14-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="bfa14-107">Daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="bfa14-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="bfa14-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfa14-108">Setting name</span></span> | <span data-ttu-id="bfa14-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfa14-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfa14-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfa14-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="bfa14-111">`false`-kültürel verilerine erişim</span><span class="sxs-lookup"><span data-stu-id="bfa14-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="bfa14-112">`true`-sabit modda çalıştır</span><span class="sxs-lookup"><span data-stu-id="bfa14-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="bfa14-113">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="bfa14-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="bfa14-114">`false`-kültürel verilerine erişim</span><span class="sxs-lookup"><span data-stu-id="bfa14-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="bfa14-115">`true`-sabit modda çalıştır</span><span class="sxs-lookup"><span data-stu-id="bfa14-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="bfa14-116">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfa14-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="bfa14-117">`0`-kültürel verilerine erişim</span><span class="sxs-lookup"><span data-stu-id="bfa14-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="bfa14-118">`1`-sabit modda çalıştır</span><span class="sxs-lookup"><span data-stu-id="bfa14-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="bfa14-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="bfa14-119">Examples</span></span>

<span data-ttu-id="bfa14-120">*runtimeconfig. JSON* dosyası:</span><span class="sxs-lookup"><span data-stu-id="bfa14-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="bfa14-121">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="bfa14-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="bfa14-122">Dönem yıl aralıkları</span><span class="sxs-lookup"><span data-stu-id="bfa14-122">Era year ranges</span></span>

- <span data-ttu-id="bfa14-123">Birden çok dönemi destekleyen takvimler için Aralık denetimlerinin gevşek olup olmadığını veya bir dönem tarih aralığını taşan tarihlerin <xref:System.ArgumentOutOfRangeException>oluşturmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="bfa14-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="bfa14-124">Varsayılan: Aralık denetimleri gevşek (`false`).</span><span class="sxs-lookup"><span data-stu-id="bfa14-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="bfa14-125">Daha fazla bilgi için bkz. [takvimler, eras ve tarih aralıkları: gevşek Aralık denetimleri](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="bfa14-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="bfa14-126">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfa14-126">Setting name</span></span> | <span data-ttu-id="bfa14-127">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfa14-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfa14-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfa14-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="bfa14-129">`false` gevşek Aralık denetimleri</span><span class="sxs-lookup"><span data-stu-id="bfa14-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="bfa14-130">`true`-taşmalar özel duruma neden olur</span><span class="sxs-lookup"><span data-stu-id="bfa14-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="bfa14-131">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfa14-131">**Environment variable**</span></span> | <span data-ttu-id="bfa14-132">YOK</span><span class="sxs-lookup"><span data-stu-id="bfa14-132">N/A</span></span> | <span data-ttu-id="bfa14-133">YOK</span><span class="sxs-lookup"><span data-stu-id="bfa14-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="bfa14-134">Japonca Tarih ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="bfa14-134">Japanese date parsing</span></span>

- <span data-ttu-id="bfa14-135">Yıl olarak "1" veya "gannen" içeren bir dizenin başarıyla ayrıştıranıp desteklenmediğini veya yalnızca "1" desteklenip desteklenmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bfa14-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="bfa14-136">Varsayılan: yıl (`false`) olarak "1" veya "gannen" içeren dizeleri ayrıştırın.</span><span class="sxs-lookup"><span data-stu-id="bfa14-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="bfa14-137">Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.</span><span class="sxs-lookup"><span data-stu-id="bfa14-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="bfa14-138">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfa14-138">Setting name</span></span> | <span data-ttu-id="bfa14-139">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfa14-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfa14-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfa14-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="bfa14-141">`false`-"gannen" veya "1" destekleniyor</span><span class="sxs-lookup"><span data-stu-id="bfa14-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="bfa14-142">`true`-yalnızca "1" destekleniyor</span><span class="sxs-lookup"><span data-stu-id="bfa14-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="bfa14-143">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfa14-143">**Environment variable**</span></span> | <span data-ttu-id="bfa14-144">YOK</span><span class="sxs-lookup"><span data-stu-id="bfa14-144">N/A</span></span> | <span data-ttu-id="bfa14-145">YOK</span><span class="sxs-lookup"><span data-stu-id="bfa14-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="bfa14-146">Japon yıl biçimi</span><span class="sxs-lookup"><span data-stu-id="bfa14-146">Japanese year format</span></span>

- <span data-ttu-id="bfa14-147">Japonca takvim çağının ilk yılının "gannen" olarak mı yoksa sayı olarak mı biçimlendirildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="bfa14-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="bfa14-148">Varsayılan: ilk yılı "gannen" (`false`) olarak biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="bfa14-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="bfa14-149">Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.</span><span class="sxs-lookup"><span data-stu-id="bfa14-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="bfa14-150">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="bfa14-150">Setting name</span></span> | <span data-ttu-id="bfa14-151">Değerler</span><span class="sxs-lookup"><span data-stu-id="bfa14-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="bfa14-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="bfa14-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="bfa14-153">`false`-"gannen" olarak Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="bfa14-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="bfa14-154">`true`-sayı olarak Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="bfa14-154">`true` - format as number</span></span> |
| <span data-ttu-id="bfa14-155">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="bfa14-155">**Environment variable**</span></span> | <span data-ttu-id="bfa14-156">YOK</span><span class="sxs-lookup"><span data-stu-id="bfa14-156">N/A</span></span> | <span data-ttu-id="bfa14-157">YOK</span><span class="sxs-lookup"><span data-stu-id="bfa14-157">N/A</span></span> |

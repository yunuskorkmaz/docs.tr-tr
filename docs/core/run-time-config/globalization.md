---
title: Küreselleşme config ayarları
description: Bir .NET Core uygulamasının küreselleşme yönlerini yapılandıran çalışma zamanı ayarları hakkında bilgi edinin, örneğin Japonca tarihleri nasıl ayrıştırdığı hakkında bilgi edinin.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733458"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="fec18-103">Küreselleşme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fec18-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="fec18-104">Değişmez mod</span><span class="sxs-lookup"><span data-stu-id="fec18-104">Invariant mode</span></span>

- <span data-ttu-id="fec18-105">Bir .NET Core uygulamasının kültüre özgü verilere ve davranışlara erişmeden küreselleşme değişmez modunda çalışıp çalışmadığını veya kültürel verilere erişimi olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fec18-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="fec18-106">Varsayılan: Uygulamayı kültürel verilere erişerek`false`çalıştırın ( ).</span><span class="sxs-lookup"><span data-stu-id="fec18-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="fec18-107">Daha fazla bilgi için [bkz.](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)</span><span class="sxs-lookup"><span data-stu-id="fec18-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="fec18-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="fec18-108">Setting name</span></span> | <span data-ttu-id="fec18-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="fec18-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fec18-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="fec18-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="fec18-111">`false`- kültürel verilere erişim</span><span class="sxs-lookup"><span data-stu-id="fec18-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="fec18-112">`true`- değişmez modda çalıştırın</span><span class="sxs-lookup"><span data-stu-id="fec18-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="fec18-113">**MSBuild özelliği**</span><span class="sxs-lookup"><span data-stu-id="fec18-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="fec18-114">`false`- kültürel verilere erişim</span><span class="sxs-lookup"><span data-stu-id="fec18-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="fec18-115">`true`- değişmez modda çalıştırın</span><span class="sxs-lookup"><span data-stu-id="fec18-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="fec18-116">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="fec18-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="fec18-117">`0`- kültürel verilere erişim</span><span class="sxs-lookup"><span data-stu-id="fec18-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="fec18-118">`1`- değişmez modda çalıştırın</span><span class="sxs-lookup"><span data-stu-id="fec18-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="fec18-119">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fec18-119">Examples</span></span>

<span data-ttu-id="fec18-120">*runtimeconfig.json* dosyası:</span><span class="sxs-lookup"><span data-stu-id="fec18-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="fec18-121">Proje dosyası:</span><span class="sxs-lookup"><span data-stu-id="fec18-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="fec18-122">Dönem yıl aralıkları</span><span class="sxs-lookup"><span data-stu-id="fec18-122">Era year ranges</span></span>

- <span data-ttu-id="fec18-123">Birden çok dönemi destekleyen takvimler için aralık denetimlerinin rahat olup olmadığını veya bir dönemin <xref:System.ArgumentOutOfRangeException>tarih aralığını tarayan tarihlerin bir .</span><span class="sxs-lookup"><span data-stu-id="fec18-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="fec18-124">Varsayılan: Aralık denetimleri`false`rahat ( ).</span><span class="sxs-lookup"><span data-stu-id="fec18-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="fec18-125">Daha fazla bilgi için [Takvimler, eralar ve tarih aralıklarına bakın: Rahat aralık denetimleri.](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)</span><span class="sxs-lookup"><span data-stu-id="fec18-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="fec18-126">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="fec18-126">Setting name</span></span> | <span data-ttu-id="fec18-127">Değerler</span><span class="sxs-lookup"><span data-stu-id="fec18-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fec18-128">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="fec18-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="fec18-129">`false`- rahat aralık kontrolleri</span><span class="sxs-lookup"><span data-stu-id="fec18-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="fec18-130">`true`- taşmalar bir özel durum neden</span><span class="sxs-lookup"><span data-stu-id="fec18-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="fec18-131">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="fec18-131">**Environment variable**</span></span> | <span data-ttu-id="fec18-132">Yok</span><span class="sxs-lookup"><span data-stu-id="fec18-132">N/A</span></span> | <span data-ttu-id="fec18-133">Yok</span><span class="sxs-lookup"><span data-stu-id="fec18-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="fec18-134">Japon tarih ayrışma</span><span class="sxs-lookup"><span data-stu-id="fec18-134">Japanese date parsing</span></span>

- <span data-ttu-id="fec18-135">Yıl başarılı bir şekilde parses olarak "1" veya "Gannen" içeren bir dize ya da sadece "1" desteklenir olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fec18-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="fec18-136">Varsayılan: Yıl olarak "1" veya "Gannen" içeren ayrıştırıcı dizeleri (`false`).</span><span class="sxs-lookup"><span data-stu-id="fec18-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="fec18-137">Daha fazla bilgi için, [birden çok erya sahip takvimlerde temsil tarihlerine](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)bakın.</span><span class="sxs-lookup"><span data-stu-id="fec18-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="fec18-138">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="fec18-138">Setting name</span></span> | <span data-ttu-id="fec18-139">Değerler</span><span class="sxs-lookup"><span data-stu-id="fec18-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fec18-140">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="fec18-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="fec18-141">`false`- "Gannen" veya "1" desteklenir</span><span class="sxs-lookup"><span data-stu-id="fec18-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="fec18-142">`true`- sadece "1" desteklenir</span><span class="sxs-lookup"><span data-stu-id="fec18-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="fec18-143">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="fec18-143">**Environment variable**</span></span> | <span data-ttu-id="fec18-144">Yok</span><span class="sxs-lookup"><span data-stu-id="fec18-144">N/A</span></span> | <span data-ttu-id="fec18-145">Yok</span><span class="sxs-lookup"><span data-stu-id="fec18-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="fec18-146">Japonca yıl biçimi</span><span class="sxs-lookup"><span data-stu-id="fec18-146">Japanese year format</span></span>

- <span data-ttu-id="fec18-147">Bir Japon takvim döneminin ilk yılının "Gannen" olarak mı yoksa sayı olarak mı biçimlendirilir sini belirler.</span><span class="sxs-lookup"><span data-stu-id="fec18-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="fec18-148">Varsayılan: İlk yılı "Gannen"`false`( ) olarak biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="fec18-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="fec18-149">Daha fazla bilgi için, [birden çok erya sahip takvimlerde temsil tarihlerine](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)bakın.</span><span class="sxs-lookup"><span data-stu-id="fec18-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="fec18-150">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="fec18-150">Setting name</span></span> | <span data-ttu-id="fec18-151">Değerler</span><span class="sxs-lookup"><span data-stu-id="fec18-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="fec18-152">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="fec18-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="fec18-153">`false`- "Gannen" olarak biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="fec18-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="fec18-154">`true`- sayı olarak biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="fec18-154">`true` - format as number</span></span> |
| <span data-ttu-id="fec18-155">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="fec18-155">**Environment variable**</span></span> | <span data-ttu-id="fec18-156">Yok</span><span class="sxs-lookup"><span data-stu-id="fec18-156">N/A</span></span> | <span data-ttu-id="fec18-157">Yok</span><span class="sxs-lookup"><span data-stu-id="fec18-157">N/A</span></span> |

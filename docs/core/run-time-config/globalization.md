---
title: Genelleştirme yapılandırma ayarları
description: .NET Core uygulamasının Genelleştirme yönlerini yapılandıran çalışma zamanı ayarları hakkında bilgi edinin. Örneğin, Japonca tarihleri nasıl ayrıştırır.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 76cd4a0a0f93f4df3ff243c6024b952576e8e6cb
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740545"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="b2813-103">Genelleştirme için çalışma zamanı yapılandırma seçenekleri</span><span class="sxs-lookup"><span data-stu-id="b2813-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="b2813-104">Sabit mod</span><span class="sxs-lookup"><span data-stu-id="b2813-104">Invariant mode</span></span>

- <span data-ttu-id="b2813-105">.NET Core uygulamasının kültüre özgü verilere ve davranışa erişim olmadan Genelleştirme sabit modunda çalışıp çalışmadığını ya da kültürel verilerine erişip erişemeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="b2813-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="b2813-106">Varsayılan: uygulamayı, kültürel verileri (`false`) erişimi ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b2813-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="b2813-107">Daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="b2813-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="b2813-108">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="b2813-108">Setting name</span></span> | <span data-ttu-id="b2813-109">Değerler</span><span class="sxs-lookup"><span data-stu-id="b2813-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b2813-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b2813-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="b2813-111">`false`-kültürel verilerine erişim</span><span class="sxs-lookup"><span data-stu-id="b2813-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="b2813-112">`true`-sabit modda çalıştır</span><span class="sxs-lookup"><span data-stu-id="b2813-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="b2813-113">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="b2813-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="b2813-114">`0`-kültürel verilerine erişim</span><span class="sxs-lookup"><span data-stu-id="b2813-114">`0` - access to cultural data</span></span><br/><span data-ttu-id="b2813-115">`1`-sabit modda çalıştır</span><span class="sxs-lookup"><span data-stu-id="b2813-115">`1` - run in invariant mode</span></span> |

## <a name="era-year-ranges"></a><span data-ttu-id="b2813-116">Dönem yıl aralıkları</span><span class="sxs-lookup"><span data-stu-id="b2813-116">Era year ranges</span></span>

- <span data-ttu-id="b2813-117">Birden çok dönemi destekleyen takvimler için Aralık denetimlerinin gevşek olup olmadığını veya bir dönem tarih aralığını taşan tarihlerin <xref:System.ArgumentOutOfRangeException>oluşturmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="b2813-117">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="b2813-118">Varsayılan: Aralık denetimleri gevşek (`false`).</span><span class="sxs-lookup"><span data-stu-id="b2813-118">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="b2813-119">Daha fazla bilgi için bkz. [takvimler, eras ve tarih aralıkları: gevşek Aralık denetimleri](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="b2813-119">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="b2813-120">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="b2813-120">Setting name</span></span> | <span data-ttu-id="b2813-121">Değerler</span><span class="sxs-lookup"><span data-stu-id="b2813-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b2813-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b2813-122">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="b2813-123">`false` gevşek Aralık denetimleri</span><span class="sxs-lookup"><span data-stu-id="b2813-123">`false` - relaxed range checks</span></span><br/><span data-ttu-id="b2813-124">`true`-taşmalar özel duruma neden olur</span><span class="sxs-lookup"><span data-stu-id="b2813-124">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="b2813-125">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="b2813-125">**Environment variable**</span></span> | <span data-ttu-id="b2813-126">YOK</span><span class="sxs-lookup"><span data-stu-id="b2813-126">N/A</span></span> | <span data-ttu-id="b2813-127">YOK</span><span class="sxs-lookup"><span data-stu-id="b2813-127">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="b2813-128">Japonca Tarih ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="b2813-128">Japanese date parsing</span></span>

- <span data-ttu-id="b2813-129">Yıl olarak "1" veya "gannen" içeren bir dizenin başarıyla ayrıştıranıp desteklenmediğini veya yalnızca "1" desteklenip desteklenmediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="b2813-129">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="b2813-130">Varsayılan: yıl (`false`) olarak "1" veya "gannen" içeren dizeleri ayrıştırın.</span><span class="sxs-lookup"><span data-stu-id="b2813-130">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="b2813-131">Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.</span><span class="sxs-lookup"><span data-stu-id="b2813-131">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="b2813-132">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="b2813-132">Setting name</span></span> | <span data-ttu-id="b2813-133">Değerler</span><span class="sxs-lookup"><span data-stu-id="b2813-133">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b2813-134">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b2813-134">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="b2813-135">`false`-"gannen" veya "1" destekleniyor</span><span class="sxs-lookup"><span data-stu-id="b2813-135">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="b2813-136">`true`-yalnızca "1" destekleniyor</span><span class="sxs-lookup"><span data-stu-id="b2813-136">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="b2813-137">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="b2813-137">**Environment variable**</span></span> | <span data-ttu-id="b2813-138">YOK</span><span class="sxs-lookup"><span data-stu-id="b2813-138">N/A</span></span> | <span data-ttu-id="b2813-139">YOK</span><span class="sxs-lookup"><span data-stu-id="b2813-139">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="b2813-140">Japon yıl biçimi</span><span class="sxs-lookup"><span data-stu-id="b2813-140">Japanese year format</span></span>

- <span data-ttu-id="b2813-141">Japonca takvim çağının ilk yılının "gannen" olarak mı yoksa sayı olarak mı biçimlendirildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="b2813-141">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="b2813-142">Varsayılan: ilk yılı "gannen" (`false`) olarak biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="b2813-142">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="b2813-143">Daha fazla bilgi için bkz. [birden çok dönemi ile takvimlerdeki tarihleri temsil](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)etme.</span><span class="sxs-lookup"><span data-stu-id="b2813-143">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="b2813-144">Ayar adı</span><span class="sxs-lookup"><span data-stu-id="b2813-144">Setting name</span></span> | <span data-ttu-id="b2813-145">Değerler</span><span class="sxs-lookup"><span data-stu-id="b2813-145">Values</span></span> |
| - | - | - |
| <span data-ttu-id="b2813-146">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="b2813-146">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="b2813-147">`false`-"gannen" olarak Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="b2813-147">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="b2813-148">`true`-sayı olarak Biçimlendir</span><span class="sxs-lookup"><span data-stu-id="b2813-148">`true` - format as number</span></span> |
| <span data-ttu-id="b2813-149">**Ortam değişkeni**</span><span class="sxs-lookup"><span data-stu-id="b2813-149">**Environment variable**</span></span> | <span data-ttu-id="b2813-150">YOK</span><span class="sxs-lookup"><span data-stu-id="b2813-150">N/A</span></span> | <span data-ttu-id="b2813-151">YOK</span><span class="sxs-lookup"><span data-stu-id="b2813-151">N/A</span></span> |

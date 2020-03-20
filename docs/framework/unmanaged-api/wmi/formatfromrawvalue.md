---
title: FormatFromRawValue fonksiyonu (Yönetilmeyen API Başvurusu)
description: FormatFromRawValue işlevi ham performans verilerini belirli bir biçime dönüştürür.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176844"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="7c28e-103">FormatFromRawValue işlevi</span><span class="sxs-lookup"><span data-stu-id="7c28e-103">FormatFromRawValue function</span></span>
<span data-ttu-id="7c28e-104">Biçim dönüştürme zamana dayalıysa, bir ham performans veri değerini belirtilen biçime veya iki ham performans veri değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="7c28e-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7c28e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c28e-105">Syntax</span></span>

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a><span data-ttu-id="7c28e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c28e-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="7c28e-107">[içinde] Sayaç türü.</span><span class="sxs-lookup"><span data-stu-id="7c28e-107">[in] The counter type.</span></span> <span data-ttu-id="7c28e-108">Sayaç türlerinin listesi için [WMI Performans Sayacı Türleri'ne](/windows/desktop/WmiSdk/wmi-performance-counter-types)bakın.</span><span class="sxs-lookup"><span data-stu-id="7c28e-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="7c28e-109">`dwCounterType`dışında herhangi bir sayaç `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`türü olabilir ve .</span><span class="sxs-lookup"><span data-stu-id="7c28e-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span>

`dwFormat`\
<span data-ttu-id="7c28e-110">[içinde] Ham performans verilerini dönüştürmek için biçim.</span><span class="sxs-lookup"><span data-stu-id="7c28e-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="7c28e-111">Aşağıdaki değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="7c28e-111">It can be one of the following values:</span></span>

|<span data-ttu-id="7c28e-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="7c28e-112">Constant</span></span>  |<span data-ttu-id="7c28e-113">Değer</span><span class="sxs-lookup"><span data-stu-id="7c28e-113">Value</span></span>  |<span data-ttu-id="7c28e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c28e-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="7c28e-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="7c28e-115">0x00000200</span></span> | <span data-ttu-id="7c28e-116">Hesaplanan değeri çift duyarlıklı kayan nokta değeri olarak döndürün.</span><span class="sxs-lookup"><span data-stu-id="7c28e-116">Return the calculated value as a double-precision floating point value.</span></span> |
| `PDH_FMT_LARGE` | <span data-ttu-id="7c28e-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="7c28e-117">0x00000400</span></span> | <span data-ttu-id="7c28e-118">Hesaplanan değeri 64 bit tamsayı olarak döndürün.</span><span class="sxs-lookup"><span data-stu-id="7c28e-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="7c28e-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="7c28e-119">0x00000100</span></span> | <span data-ttu-id="7c28e-120">Hesaplanan değeri 32 bit tamsayı olarak döndürün.</span><span class="sxs-lookup"><span data-stu-id="7c28e-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="7c28e-121">Önceki değerlerden biri, aşağıdaki ölçekleme bayraklarından biriyle ORed olabilir:</span><span class="sxs-lookup"><span data-stu-id="7c28e-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="7c28e-122">Sabit</span><span class="sxs-lookup"><span data-stu-id="7c28e-122">Constant</span></span>  |<span data-ttu-id="7c28e-123">Değer</span><span class="sxs-lookup"><span data-stu-id="7c28e-123">Value</span></span>  |<span data-ttu-id="7c28e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c28e-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="7c28e-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="7c28e-125">0x00001000</span></span> | <span data-ttu-id="7c28e-126">Sayacın ölçekleme faktörlerini uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="7c28e-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="7c28e-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="7c28e-127">0x00002000</span></span> | <span data-ttu-id="7c28e-128">Son değeri 1.000 ile çarpın.</span><span class="sxs-lookup"><span data-stu-id="7c28e-128">Multiply the final value by 1,000.</span></span> |

`pTimeBase`\
<span data-ttu-id="7c28e-129">[içinde] Biçim dönüştürme için gerekirse zaman tabanına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c28e-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="7c28e-130">Biçim dönüştürme için zaman temel bilgileri gerekli değilse, bu parametrenin değeri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="7c28e-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

`pRawValue1`\
<span data-ttu-id="7c28e-131">[içinde] Ham performans [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) değerini temsil eden bir yapının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7c28e-131">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="7c28e-132">[içinde] İkinci ham [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) performans değerini temsil eden bir yapının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7c28e-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="7c28e-133">İkinci bir ham performans değeri gerekli değilse, `null`bu parametre .</span><span class="sxs-lookup"><span data-stu-id="7c28e-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="7c28e-134">[çıkış] Biçimlendirilmiş performans [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) değerini alan bir yapının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7c28e-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="7c28e-135">Döndürülen değer</span><span class="sxs-lookup"><span data-stu-id="7c28e-135">Return value</span></span>

<span data-ttu-id="7c28e-136">Aşağıdaki değerler bu işlevle döndürülür:</span><span class="sxs-lookup"><span data-stu-id="7c28e-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="7c28e-137">Sabit</span><span class="sxs-lookup"><span data-stu-id="7c28e-137">Constant</span></span>  |<span data-ttu-id="7c28e-138">Değer</span><span class="sxs-lookup"><span data-stu-id="7c28e-138">Value</span></span>  |<span data-ttu-id="7c28e-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c28e-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="7c28e-140">0</span><span class="sxs-lookup"><span data-stu-id="7c28e-140">0</span></span> | <span data-ttu-id="7c28e-141">İşlev çağrısı başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="7c28e-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="7c28e-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="7c28e-142">0xC0000BBD</span></span> | <span data-ttu-id="7c28e-143">Gerekli bir bağımsız değişken eksik veya yanlış.</span><span class="sxs-lookup"><span data-stu-id="7c28e-143">A required argument is missing or incorrect.</span></span> |
| `PDH_INVALID_HANDLE` | <span data-ttu-id="7c28e-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="7c28e-144">0xC0000BBC</span></span> | <span data-ttu-id="7c28e-145">Tanıtıcı geçerli bir PDH nesnesi değildir.</span><span class="sxs-lookup"><span data-stu-id="7c28e-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7c28e-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c28e-146">Remarks</span></span>

<span data-ttu-id="7c28e-147">Bu [işlev, FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) işlevine bir çağrı yıkıyor.</span><span class="sxs-lookup"><span data-stu-id="7c28e-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c28e-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c28e-148">Requirements</span></span>

 <span data-ttu-id="7c28e-149">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c28e-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="7c28e-150">**Kütüphane:** Perfcounter.dll</span><span class="sxs-lookup"><span data-stu-id="7c28e-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="7c28e-151">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7c28e-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7c28e-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c28e-152">See also</span></span>

- [<span data-ttu-id="7c28e-153">WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7c28e-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

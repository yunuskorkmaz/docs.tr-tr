---
title: FormatFromRawValue işlevi (yönetilmeyen API Başvurusu)
description: FormatFromRawValue işlevi, ham performans verilerini belirtilen biçime dönüştürür.
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
ms.openlocfilehash: 5097cfe43ae785461a1e2af1217bcbd5e8c4b79c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120280"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="bbc38-103">FormatFromRawValue işlevi</span><span class="sxs-lookup"><span data-stu-id="bbc38-103">FormatFromRawValue function</span></span>
<span data-ttu-id="bbc38-104">Biçim dönüştürmesi zaman tabanlıysa, bir ham performans verisi değerini belirtilen biçime veya iki ham performans verisi değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bbc38-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bbc38-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbc38-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="bbc38-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbc38-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="bbc38-107">'ndaki Sayaç türü.</span><span class="sxs-lookup"><span data-stu-id="bbc38-107">[in] The counter type.</span></span> <span data-ttu-id="bbc38-108">Sayaç türlerinin listesi için bkz. [WMI performans sayacı türleri](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="bbc38-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="bbc38-109">`dwCounterType`, `PERF_LARGE_RAW_FRACTION` ve `PERF_LARGE_RAW_BASE`dışında herhangi bir sayaç türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="bbc38-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="bbc38-110">'ndaki Ham performans verilerinin dönüştürüleceği biçim.</span><span class="sxs-lookup"><span data-stu-id="bbc38-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="bbc38-111">Aşağıdaki değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="bbc38-111">It can be one of the following values:</span></span>

|<span data-ttu-id="bbc38-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="bbc38-112">Constant</span></span>  |<span data-ttu-id="bbc38-113">Değer</span><span class="sxs-lookup"><span data-stu-id="bbc38-113">Value</span></span>  |<span data-ttu-id="bbc38-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc38-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="bbc38-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="bbc38-115">0x00000200</span></span> | <span data-ttu-id="bbc38-116">Hesaplanan değeri çift duyarlıklı kayan nokta değeri olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc38-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="bbc38-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="bbc38-117">0x00000400</span></span> | <span data-ttu-id="bbc38-118">Hesaplanan değeri 64 bitlik bir tamsayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc38-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="bbc38-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="bbc38-119">0x00000100</span></span> | <span data-ttu-id="bbc38-120">Hesaplanan değeri 32 bitlik bir tamsayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc38-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="bbc38-121">Önceki değerlerden biri aşağıdaki ölçeklendirme bayraklarından biriyle ORed olabilir:</span><span class="sxs-lookup"><span data-stu-id="bbc38-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="bbc38-122">Sabit</span><span class="sxs-lookup"><span data-stu-id="bbc38-122">Constant</span></span>  |<span data-ttu-id="bbc38-123">Değer</span><span class="sxs-lookup"><span data-stu-id="bbc38-123">Value</span></span>  |<span data-ttu-id="bbc38-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc38-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="bbc38-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="bbc38-125">0x00001000</span></span> | <span data-ttu-id="bbc38-126">Sayacın ölçeklendirme faktörlerini uygulamayın.</span><span class="sxs-lookup"><span data-stu-id="bbc38-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="bbc38-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="bbc38-127">0x00002000</span></span> | <span data-ttu-id="bbc38-128">Son değeri 1.000 ile çarpın.</span><span class="sxs-lookup"><span data-stu-id="bbc38-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="bbc38-129">'ndaki Biçim dönüştürmesi için gerekliyse, zaman tabanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bbc38-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="bbc38-130">Biçim dönüştürmesi için zaman taban bilgileri gerekli değilse, bu parametrenin değeri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="bbc38-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="bbc38-131">`pRawValue1`\ [in] bir ham performans değerini temsil eden [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) yapısına yönelik bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="bbc38-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="bbc38-132">'ndaki İkinci bir ham performans değerini temsil eden [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bbc38-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="bbc38-133">İkinci bir ham performans değeri gerekli değilse, bu parametrenin `null`olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bbc38-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="bbc38-134">dışı Biçimli performans değerini alan [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bbc38-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="bbc38-135">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="bbc38-135">Return value</span></span>

<span data-ttu-id="bbc38-136">Aşağıdaki değerler bu işlev tarafından döndürülür:</span><span class="sxs-lookup"><span data-stu-id="bbc38-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="bbc38-137">Sabit</span><span class="sxs-lookup"><span data-stu-id="bbc38-137">Constant</span></span>  |<span data-ttu-id="bbc38-138">Değer</span><span class="sxs-lookup"><span data-stu-id="bbc38-138">Value</span></span>  |<span data-ttu-id="bbc38-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc38-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="bbc38-140">0</span><span class="sxs-lookup"><span data-stu-id="bbc38-140">0</span></span> | <span data-ttu-id="bbc38-141">İşlev çağrısı başarılı.</span><span class="sxs-lookup"><span data-stu-id="bbc38-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="bbc38-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="bbc38-142">0xC0000BBD</span></span> | <span data-ttu-id="bbc38-143">Gerekli bir bağımsız değişken eksik veya yanlış.</span><span class="sxs-lookup"><span data-stu-id="bbc38-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="bbc38-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="bbc38-144">0xC0000BBC</span></span> | <span data-ttu-id="bbc38-145">Tanıtıcı geçerli bir PDH nesnesi değil.</span><span class="sxs-lookup"><span data-stu-id="bbc38-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bbc38-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbc38-146">Remarks</span></span>

<span data-ttu-id="bbc38-147">Bu işlev, [Formatfromrawvalue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) işlevine bir çağrı kaydırır.</span><span class="sxs-lookup"><span data-stu-id="bbc38-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbc38-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbc38-148">Requirements</span></span>

 <span data-ttu-id="bbc38-149">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbc38-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bbc38-150">**Kitaplık:** PerfCounter. dll</span><span class="sxs-lookup"><span data-stu-id="bbc38-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="bbc38-151">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bbc38-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bbc38-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbc38-152">See also</span></span>

- [<span data-ttu-id="bbc38-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="bbc38-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

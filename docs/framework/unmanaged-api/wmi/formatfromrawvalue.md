---
title: FormatFromRawValue işlevi (yönetilmeyen API Başvurusu)
description: FormatFromRawValue işlevi ham performans verilerini belirtilen bir biçime dönüştürür.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 420a02d2f7757c52d6e8ff92a9ca30e44938cd18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546445"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="e98f8-103">FormatFromRawValue işlevi</span><span class="sxs-lookup"><span data-stu-id="e98f8-103">FormatFromRawValue function</span></span>
<span data-ttu-id="e98f8-104">Biçim dönüştürme, zamana bağlı ise belirtilen biçimde bir ham performans veri değerine ya da iki ham performans veri değerleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e98f8-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="e98f8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e98f8-105">Syntax</span></span>  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a><span data-ttu-id="e98f8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e98f8-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="e98f8-107">[in] Sayaç türü.</span><span class="sxs-lookup"><span data-stu-id="e98f8-107">[in] The counter type.</span></span> <span data-ttu-id="e98f8-108">Sayaç türlerinin bir listesi için bkz. [WMI performansı sayaç türleri](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="e98f8-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="e98f8-109">`dwCounterType` dışında herhangi bir sayaç türü olabilir `PERF_LARGE_RAW_FRACTION` ve `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="e98f8-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="e98f8-110">[in] Ham performans dönüştürülecek biçimi.</span><span class="sxs-lookup"><span data-stu-id="e98f8-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="e98f8-111">Aşağıdaki değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="e98f8-111">It can be one of the following values:</span></span>

|<span data-ttu-id="e98f8-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="e98f8-112">Constant</span></span>  |<span data-ttu-id="e98f8-113">Değer</span><span class="sxs-lookup"><span data-stu-id="e98f8-113">Value</span></span>  |<span data-ttu-id="e98f8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e98f8-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="e98f8-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="e98f8-115">0x00000200</span></span> | <span data-ttu-id="e98f8-116">Hesaplanan değer bir çift duyarlıklı kayan noktalı değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e98f8-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="e98f8-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="e98f8-117">0x00000400</span></span> | <span data-ttu-id="e98f8-118">Hesaplanan değeri bir 64-bit tamsayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="e98f8-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="e98f8-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="e98f8-119">0x00000100</span></span> | <span data-ttu-id="e98f8-120">Hesaplanan değer 32-bit tamsayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="e98f8-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="e98f8-121">Önceki değerlerinden ORed aşağıdaki ölçeklendirme bayrakları birine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="e98f8-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="e98f8-122">Sabit</span><span class="sxs-lookup"><span data-stu-id="e98f8-122">Constant</span></span>  |<span data-ttu-id="e98f8-123">Değer</span><span class="sxs-lookup"><span data-stu-id="e98f8-123">Value</span></span>  |<span data-ttu-id="e98f8-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e98f8-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="e98f8-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="e98f8-125">0x00001000</span></span> | <span data-ttu-id="e98f8-126">Sayacın ölçekleme faktörü geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e98f8-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="e98f8-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="e98f8-127">0x00002000</span></span> | <span data-ttu-id="e98f8-128">Son değer 1000 ile çarpın.</span><span class="sxs-lookup"><span data-stu-id="e98f8-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="e98f8-129">[in] Süresi Temeli, biçim dönüştürme için gerekirse bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e98f8-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="e98f8-130">Saat temel bilgileri, biçim dönüştürme için gerekli değildir, bu parametrenin değeri yok sayıldı.</span><span class="sxs-lookup"><span data-stu-id="e98f8-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="e98f8-131">`pRawValue1` [in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) ham performans değerini temsil eden yapısı.</span><span class="sxs-lookup"><span data-stu-id="e98f8-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a raw performance value.</span></span>

<span data-ttu-id="e98f8-132">`pRawValue2` [in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) ikinci bir performans değeri temsil eden yapısı.</span><span class="sxs-lookup"><span data-stu-id="e98f8-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="e98f8-133">İkinci bir ham performans değeri gerekli değilse bu parametre olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="e98f8-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="e98f8-134">`pFmtValue` [out] Bir işaretçi bir [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) biçimlendirilmiş bir performans değeri alan yapısı.</span><span class="sxs-lookup"><span data-stu-id="e98f8-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="e98f8-135">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="e98f8-135">Return value</span></span>

<span data-ttu-id="e98f8-136">Aşağıdaki değerlerden bu işlev tarafından döndürülen:</span><span class="sxs-lookup"><span data-stu-id="e98f8-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="e98f8-137">Sabit</span><span class="sxs-lookup"><span data-stu-id="e98f8-137">Constant</span></span>  |<span data-ttu-id="e98f8-138">Değer</span><span class="sxs-lookup"><span data-stu-id="e98f8-138">Value</span></span>  |<span data-ttu-id="e98f8-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e98f8-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="e98f8-140">0</span><span class="sxs-lookup"><span data-stu-id="e98f8-140">0</span></span> | <span data-ttu-id="e98f8-141">İşlev çağrısı başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="e98f8-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="e98f8-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="e98f8-142">0xC0000BBD</span></span> | <span data-ttu-id="e98f8-143">Gerekli bir bağımsız değişken eksik ya da yanlış biçimlendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="e98f8-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="e98f8-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="e98f8-144">0xC0000BBC</span></span> | <span data-ttu-id="e98f8-145">Tanıtıcı geçerli bir PDH nesnesi değil.</span><span class="sxs-lookup"><span data-stu-id="e98f8-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="e98f8-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e98f8-146">Remarks</span></span>

<span data-ttu-id="e98f8-147">Bu işlev bir çağrı sarılır [FormatFromRawValue](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms231047%28v=vs.85%29) işlevi.</span><span class="sxs-lookup"><span data-stu-id="e98f8-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms231047%28v=vs.85%29) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="e98f8-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e98f8-148">Requirements</span></span>  
 <span data-ttu-id="e98f8-149">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e98f8-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e98f8-150">**Kitaplığı:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="e98f8-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="e98f8-151">**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e98f8-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e98f8-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e98f8-152">See also</span></span>
- [<span data-ttu-id="e98f8-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e98f8-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

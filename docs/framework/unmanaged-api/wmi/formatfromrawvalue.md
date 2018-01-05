---
title: "FormatFromRawValue işlevi (yönetilmeyen API Başvurusu)"
description: "FormatFromRawValue işlevi ham performans verilerini belirtilen biçime dönüştürür."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: FormatFromRawValue
api_location: PerfCounter.dll
api_type: DLLExport
f1_keywords: FormatFromRawValue
helpviewer_keywords: FormatFromRawValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3daa89ec0b40bb9c08898ecd682f05f0f0ce09a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="d8dba-103">FormatFromRawValue işlevi</span><span class="sxs-lookup"><span data-stu-id="d8dba-103">FormatFromRawValue function</span></span>
<span data-ttu-id="d8dba-104">Biçim dönüştürmeyi zamana dayalı ise belirtilen biçime bir ham performans veri değeri veya iki ham performans veri değerleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d8dba-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d8dba-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8dba-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="d8dba-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8dba-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="d8dba-107">[in] Sayaç türü.</span><span class="sxs-lookup"><span data-stu-id="d8dba-107">[in] The counter type.</span></span> <span data-ttu-id="d8dba-108">Sayaç türlerinin listesi için bkz: [WMI performansı sayaç türleri](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="d8dba-108">For a list of counter types, see [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span></span> <span data-ttu-id="d8dba-109">`dwCounterType`dışında herhangi bir sayaç türü olabilir `PERF_LARGE_RAW_FRACTION` ve `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="d8dba-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="d8dba-110">[in] Ham performans verilerini dönüştürülecek biçimi.</span><span class="sxs-lookup"><span data-stu-id="d8dba-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="d8dba-111">Aşağıdaki değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="d8dba-111">It can be one of the following values:</span></span>

|<span data-ttu-id="d8dba-112">Sabit</span><span class="sxs-lookup"><span data-stu-id="d8dba-112">Constant</span></span>  |<span data-ttu-id="d8dba-113">Değer</span><span class="sxs-lookup"><span data-stu-id="d8dba-113">Value</span></span>  |<span data-ttu-id="d8dba-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8dba-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="d8dba-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="d8dba-115">0x00000200</span></span> | <span data-ttu-id="d8dba-116">Hesaplanan değer bir çift duyarlıklı kayan noktalı değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8dba-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="d8dba-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="d8dba-117">0x00000400</span></span> | <span data-ttu-id="d8dba-118">Hesaplanan değeri bir 64-bit tamsayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8dba-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="d8dba-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="d8dba-119">0x00000100</span></span> | <span data-ttu-id="d8dba-120">Hesaplanan değer 32 bit tamsayı olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8dba-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="d8dba-121">Aşağıdaki ölçeklendirme bayraklardan biri ile bölümleri önceki değerlerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="d8dba-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="d8dba-122">Sabit</span><span class="sxs-lookup"><span data-stu-id="d8dba-122">Constant</span></span>  |<span data-ttu-id="d8dba-123">Değer</span><span class="sxs-lookup"><span data-stu-id="d8dba-123">Value</span></span>  |<span data-ttu-id="d8dba-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8dba-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="d8dba-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="d8dba-125">0x00001000</span></span> | <span data-ttu-id="d8dba-126">Sayacın ölçeklendirme etkenleri geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d8dba-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="d8dba-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="d8dba-127">0x00002000</span></span> | <span data-ttu-id="d8dba-128">Son değer tarafından 1,000 çarpın.</span><span class="sxs-lookup"><span data-stu-id="d8dba-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="d8dba-129">[in] Biçim dönüştürme için gerekiyorsa süresi temeli için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8dba-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="d8dba-130">Zamanı temel bilgileri biçimi dönüştürme için gerekli değilse, bu parametrenin değeri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="d8dba-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="d8dba-131">`pRawValue1`[in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) yapısı bir ham performans değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d8dba-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a raw performance value.</span></span>

<span data-ttu-id="d8dba-132">`pRawValue2`[in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) yapısı ikinci bir ham performans değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d8dba-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a second raw performance value.</span></span> <span data-ttu-id="d8dba-133">İkinci bir ham performans değeri gerekli değilse, bu parametre olmalıdır `null`.</span><span class="sxs-lookup"><span data-stu-id="d8dba-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="d8dba-134">`pFmtValue`[out] Bir işaretçi bir [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) yapısı biçimlendirilmiş performans değeri alır.</span><span class="sxs-lookup"><span data-stu-id="d8dba-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="d8dba-135">Dönüş değeri</span><span class="sxs-lookup"><span data-stu-id="d8dba-135">Return value</span></span>

<span data-ttu-id="d8dba-136">Aşağıdaki değerleri bu işlev tarafından döndürülen:</span><span class="sxs-lookup"><span data-stu-id="d8dba-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="d8dba-137">Sabit</span><span class="sxs-lookup"><span data-stu-id="d8dba-137">Constant</span></span>  |<span data-ttu-id="d8dba-138">Değer</span><span class="sxs-lookup"><span data-stu-id="d8dba-138">Value</span></span>  |<span data-ttu-id="d8dba-139">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8dba-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="d8dba-140">0</span><span class="sxs-lookup"><span data-stu-id="d8dba-140">0</span></span> | <span data-ttu-id="d8dba-141">İşlev çağrısı başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="d8dba-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="d8dba-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="d8dba-142">0xC0000BBD</span></span> | <span data-ttu-id="d8dba-143">Gerekli bir bağımsız değişken eksik veya yanlış.</span><span class="sxs-lookup"><span data-stu-id="d8dba-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="d8dba-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="d8dba-144">0xC0000BBC</span></span> | <span data-ttu-id="d8dba-145">Tanıtıcı geçerli bir PDH nesnesi değil.</span><span class="sxs-lookup"><span data-stu-id="d8dba-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d8dba-146">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8dba-146">Remarks</span></span>

<span data-ttu-id="d8dba-147">Bu işlev çağrısı sarmalar [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) işlevi.</span><span class="sxs-lookup"><span data-stu-id="d8dba-147">This function wraps a call to the [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8dba-148">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8dba-148">Requirements</span></span>  
 <span data-ttu-id="d8dba-149">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8dba-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8dba-150">**Kitaplığı:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="d8dba-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="d8dba-151">**.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d8dba-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8dba-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8dba-152">See also</span></span>  
[<span data-ttu-id="d8dba-153">WMI ve performans sayaçları (yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d8dba-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)

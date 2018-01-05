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
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue işlevi
Biçim dönüştürmeyi zamana dayalı ise belirtilen biçime bir ham performans veri değeri veya iki ham performans veri değerleri dönüştürür.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
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

## <a name="parameters"></a>Parametreler

`dwCounterType`  
[in] Sayaç türü. Sayaç türlerinin listesi için bkz: [WMI performansı sayaç türleri](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx). `dwCounterType`dışında herhangi bir sayaç türü olabilir `PERF_LARGE_RAW_FRACTION` ve `PERF_LARGE_RAW_BASE`. 

`dwFormat`  
[in] Ham performans verilerini dönüştürülecek biçimi. Aşağıdaki değerlerden biri olabilir:

|Sabit  |Değer  |Açıklama |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Hesaplanan değer bir çift duyarlıklı kayan noktalı değeri döndürür. | 
| `PDH_FMT_LARGE` | 0x00000400 | Hesaplanan değeri bir 64-bit tamsayı olarak döndürür. |
| `PDH_FMT_LONG` | 0x00000100 | Hesaplanan değer 32 bit tamsayı olarak döndürür. |

Aşağıdaki ölçeklendirme bayraklardan biri ile bölümleri önceki değerlerden biri olabilir:

|Sabit  |Değer  |Açıklama |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Sayacın ölçeklendirme etkenleri geçerli değildir. |
| `PDH_FMT_1000` | 0x00002000 | Son değer tarafından 1,000 çarpın. | 

`pTimeBase`  
[in] Biçim dönüştürme için gerekiyorsa süresi temeli için bir işaretçi. Zamanı temel bilgileri biçimi dönüştürme için gerekli değilse, bu parametrenin değeri göz ardı edilir.

`pRawValue1`[in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) yapısı bir ham performans değerini temsil eder.

`pRawValue2`[in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) yapısı ikinci bir ham performans değerini temsil eder. İkinci bir ham performans değeri gerekli değilse, bu parametre olmalıdır `null`.

`pFmtValue`[out] Bir işaretçi bir [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) yapısı biçimlendirilmiş performans değeri alır.

## <a name="return-value"></a>Dönüş değeri

Aşağıdaki değerleri bu işlev tarafından döndürülen:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | İşlev çağrısı başarılı olur. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Gerekli bir bağımsız değişken eksik veya yanlış. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Tanıtıcı geçerli bir PDH nesnesi değil. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Kitaplığı:** PerfCounter.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

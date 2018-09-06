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
ms.openlocfilehash: 95ef445d41672c5c2895bd7115afb6a73a57e8f9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779930"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue işlevi
Biçim dönüştürme, zamana bağlı ise belirtilen biçimde bir ham performans veri değerine ya da iki ham performans veri değerleri dönüştürür.   
  
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
[in] Sayaç türü. Sayaç türlerinin bir listesi için bkz. [WMI performansı sayaç türleri](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` dışında herhangi bir sayaç türü olabilir `PERF_LARGE_RAW_FRACTION` ve `PERF_LARGE_RAW_BASE`. 

`dwFormat`  
[in] Ham performans dönüştürülecek biçimi. Aşağıdaki değerlerden biri olabilir:

|Sabit  |Değer  |Açıklama |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Hesaplanan değer bir çift duyarlıklı kayan noktalı değer döndürür. | 
| `PDH_FMT_LARGE` | 0x00000400 | Hesaplanan değeri bir 64-bit tamsayı olarak döndürür. |
| `PDH_FMT_LONG` | 0x00000100 | Hesaplanan değer 32-bit tamsayı olarak döndürür. |

Önceki değerlerinden ORed aşağıdaki ölçeklendirme bayrakları birine sahip olabilir:

|Sabit  |Değer  |Açıklama |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Sayacın ölçekleme faktörü geçerli değildir. |
| `PDH_FMT_1000` | 0x00002000 | Son değer 1000 ile çarpın. | 

`pTimeBase`  
[in] Süresi Temeli, biçim dönüştürme için gerekirse bir işaretçi. Saat temel bilgileri, biçim dönüştürme için gerekli değildir, bu parametrenin değeri yok sayıldı.

`pRawValue1` [in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) ham performans değerini temsil eden yapısı.

`pRawValue2` [in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) ikinci bir performans değeri temsil eden yapısı. İkinci bir ham performans değeri gerekli değilse bu parametre olmalıdır `null`.

`pFmtValue` [out] Bir işaretçi bir [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) biçimlendirilmiş bir performans değeri alan yapısı.

## <a name="return-value"></a>Dönüş değeri

Aşağıdaki değerlerden bu işlev tarafından döndürülen:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | İşlev çağrısı başarılı olur. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Gerekli bir bağımsız değişken eksik ya da yanlış biçimlendirilmiş. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Tanıtıcı geçerli bir PDH nesnesi değil. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Kitaplığı:** PerfCounter.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

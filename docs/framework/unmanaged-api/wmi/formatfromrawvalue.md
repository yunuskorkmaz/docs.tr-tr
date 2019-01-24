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

`pRawValue1` [in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) ham performans değerini temsil eden yapısı.

`pRawValue2` [in] Bir işaretçi bir [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) ikinci bir performans değeri temsil eden yapısı. İkinci bir ham performans değeri gerekli değilse bu parametre olmalıdır `null`.

`pFmtValue` [out] Bir işaretçi bir [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) biçimlendirilmiş bir performans değeri alan yapısı.

## <a name="return-value"></a>Dönüş değeri

Aşağıdaki değerlerden bu işlev tarafından döndürülen:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | İşlev çağrısı başarılı olur. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Gerekli bir bağımsız değişken eksik ya da yanlış biçimlendirilmiş. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Tanıtıcı geçerli bir PDH nesnesi değil. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [FormatFromRawValue](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/ms231047%28v=vs.85%29) işlevi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Kitaplığı:** PerfCounter.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

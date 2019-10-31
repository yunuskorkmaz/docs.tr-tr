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
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue işlevi
Biçim dönüştürmesi zaman tabanlıysa, bir ham performans verisi değerini belirtilen biçime veya iki ham performans verisi değerine dönüştürür. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

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

## <a name="parameters"></a>Parametreler

`dwCounterType`\
'ndaki Sayaç türü. Sayaç türlerinin listesi için bkz. [WMI performans sayacı türleri](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType`, `PERF_LARGE_RAW_FRACTION` ve `PERF_LARGE_RAW_BASE`dışında herhangi bir sayaç türü olabilir. 

`dwFormat`\
'ndaki Ham performans verilerinin dönüştürüleceği biçim. Aşağıdaki değerlerden biri olabilir:

|Sabit  |Değer  |Açıklama |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Hesaplanan değeri çift duyarlıklı kayan nokta değeri olarak döndürür. | 
| `PDH_FMT_LARGE` | 0x00000400 | Hesaplanan değeri 64 bitlik bir tamsayı olarak döndürür. |
| `PDH_FMT_LONG` | 0x00000100 | Hesaplanan değeri 32 bitlik bir tamsayı olarak döndürür. |

Önceki değerlerden biri aşağıdaki ölçeklendirme bayraklarından biriyle ORed olabilir:

|Sabit  |Değer  |Açıklama |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Sayacın ölçeklendirme faktörlerini uygulamayın. |
| `PDH_FMT_1000` | 0x00002000 | Son değeri 1.000 ile çarpın. | 

`pTimeBase`\
'ndaki Biçim dönüştürmesi için gerekliyse, zaman tabanına yönelik bir işaretçi. Biçim dönüştürmesi için zaman taban bilgileri gerekli değilse, bu parametrenin değeri yok sayılır.

`pRawValue1`\ [in] bir ham performans değerini temsil eden [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) yapısına yönelik bir işaretçidir.

`pRawValue2`\
'ndaki İkinci bir ham performans değerini temsil eden [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) yapısına yönelik bir işaretçi. İkinci bir ham performans değeri gerekli değilse, bu parametrenin `null`olması gerekir.

`pFmtValue`\
dışı Biçimli performans değerini alan [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) yapısına yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş değeri

Aşağıdaki değerler bu işlev tarafından döndürülür:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | İşlev çağrısı başarılı. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Gerekli bir bağımsız değişken eksik veya yanlış. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Tanıtıcı geçerli bir PDH nesnesi değil. |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [Formatfromrawvalue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) işlevine bir çağrı kaydırır.

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

 **Kitaplık:** PerfCounter. dll

 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

---
title: QualifierSet_BeginEnumeration işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_BeginEnumeration işlevi, bir nesnenin niteleyicilerinin bir numaralandırıcısı sıfırlar.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b75c51ebddd78e447fed57b22a96c2d5c35004e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798351"
---
# <a name="qualifierset_beginenumeration-function"></a>QualifierSet_BeginEnumeration işlevi

Bir nesnenin niteleyicilerinin bir Numaralandırıcı, numaralandırmanın başlangıcına sıfırlanır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

`lFlags`\
'ndaki Listelemenin dahil olduğu niteleyicileri belirten [açıklamalar](#remarks) bölümünde açıklanan bayrakların veya değerlerin bit düzeyinde birleşimi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` Parametre geçerli değil. |
|`WBEM_E_UNEXPECTED` | 0x8004101D | İçin bir araya giren `QualifierSet_BeginEnumeration` [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)çağrı yapılmadan ikinci bir çağrı yapıldı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemQualifierSet:: BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) yöntemine bir çağrı kaydırır.

Bir nesnedeki tüm niteleyicileri numaralandırmak için, bu yöntemin [QualifierSet_Next](qualifierset-next.md)ilk çağrısından önce çağrılması gerekir. Niteleyicilerin numaralandırılma sırası, belirli bir numaralandırma için sabit değer olarak garanti edilir.

`lEnumFlags` Bağımsız değişken olarak geçirilebilecek bayraklar, *wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz.

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|  | 0 | Tüm niteleyicilerin adlarını döndürün. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca geçerli özelliğe veya nesneye özgü niteleyicilerin adlarını döndürür. <br/> Bir özellik için: Sınıf tanımından yayılan niteleyiciler değil, yalnızca özelliğe özgü niteleyicileri döndürün (geçersiz kılmalar dahil). <br/> Bir örnek için: Yalnızca örneğe özgü niteleyici adlarını döndürür. <br/> Bir sınıf için: Yalnızca türetmekte olan sınıfa özgü niteleyicileri döndürün.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Yalnızca başka bir nesneden yayılan niteleyicilerin adlarını döndürür. <br/> Bir özellik için: Yalnızca sınıf tanımından bu özelliğe yayılan niteleyicileri döndürün, özelliğin kendisinden değil. <br/> Bir örnek için: Yalnızca sınıf tanımından yayılan niteleyicileri döndürün. <br/> Bir sınıf için: Yalnızca üst sınıflardan devralınan niteleyici adlarını döndürür. |

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

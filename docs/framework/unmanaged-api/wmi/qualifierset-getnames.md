---
title: QualifierSet_GetNames işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_GetNames işlevi, bir nesne veya özellikten niteleyicilerin adlarını alır.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141700"
---
# <a name="qualifierset_getnames-function"></a>QualifierSet_GetNames işlevi

Geçerli nesne veya özellikten kullanılabilen tüm niteleyicilerin veya belirli niteleyicilerin adlarını alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki Bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği işaretçisi.

`lFlags`\
'ndaki Aşağıdaki bayraklardan biri veya sabit listesine hangi adların ekleneceğini belirten değerler.

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|  | 0 | Tüm niteleyicilerin adlarını döndürün. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca geçerli özelliğe veya nesneye özgü niteleyicilerin adlarını döndürür. <br/> Bir özellik için: yalnızca özelliğe özgü niteleyicileri döndürün (geçersiz kılmalar dahil), sınıf tanımından yayılan niteleyiciler değildir. <br/> Bir örnek için: yalnızca örneğe özgü niteleyici adlarını döndürür. <br/> Bir sınıf için: yalnızca türetmekte olan sınıfa özgü niteleyicileri döndürün.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Yalnızca başka bir nesneden yayılan niteleyicilerin adlarını döndürür. <br/> Bir özellik için: yalnızca sınıf tanımından bu özelliğe yayılan niteleyicileri döndürün, özelliğin kendisinden değil. <br/> Bir örnek için: yalnızca sınıf tanımından yayılan niteleyicileri döndürün. <br/> Bir sınıf için: yalnızca üst sınıflardan devralınan niteleyici adlarını döndürür. |

`pstrNames`\
dışı İstenen adları içeren yeni bir `SAFEARRAY`. Dizide 0 öğesi olabilir. Bir hata oluşursa, yeni bir `SAFEARRAY` döndürülmez.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir sabit listesi başlatmak için yeterli kullanılabilir bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemQualifierSet:: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) yöntemine bir çağrı kaydırır.

Niteleyici adlarını aldıktan sonra, [QualifierSet_Get](qualifierset-get.md) işlevini çağırarak her bir niteleyicisine ada göre erişebilirsiniz.

Belirli bir nesnenin sıfır niteleyicisi olması için bir hata değil, bu nedenle dönüşte `pstrNames` dize sayısı, işlev `WBEM_S_NO_ERROR`döndürse bile 0 olabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

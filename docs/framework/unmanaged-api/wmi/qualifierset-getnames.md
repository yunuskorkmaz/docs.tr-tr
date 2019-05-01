---
title: QualifierSet_GetNames işlevi (yönetilmeyen API Başvurusu)
description: QualifierSet_GetNames işlevi, bir nesneye veya özelliğe niteleyicileri adlarını alır.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da6321e50082c3f73477b8187cc5bf671655df21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943402"
---
# <a name="qualifiersetgetnames-function"></a>QualifierSet_GetNames function

Tüm niteleyicileri veya geçerli nesne ya da özellik mevcut olan bazı niteleyicileri adlarını alır.

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
[in] Bu parametre kullanılmaz.

`ptr`\
[in] Bir işaretçi bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) örneği.

`lFlags`\
[in] Aşağıdaki bayrakları veya numaralandırmada dahil etmek için hangi adlarını belirten değerlerinden biri.

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|  | 0 | Tüm niteleyicileri adlarını döndürür. |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Yalnızca niteleyicileri adları belirli için geçerli bir özellik veya nesne döndürür. <br/> Bir özellik için: Yalnızca (geçersiz kılmaları dahil) özelliğine belirli niteleyicileri ve olmayan sınıf tanımından yayılan niteleyicileri döndürür. <br/> Bir örneği için: Yalnızca örnek özgü niteleyicisi adlarını döndürür. <br/> Bir sınıf için: Elde sınıf niteleyicileri yalnızca belirli döndürür.
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | Başka bir nesnenin dönüş yalnızca niteleyicileri adlarını yayılır. <br/> Bir özellik için: Bu özellik yalnızca niteleyicileri yayılan dön sınıf tanımı ve özelliğinden olanlar. <br/> Bir örneği için: Sınıf tanımı dönüş niteleyicileri yalnızca yayılır. <br/> Bir sınıf için: Return bu niteleyici adları yalnızca üst sınıflardan devralınır. |

`pstrNames`\
[out] Yeni bir `SAFEARRAY` , istenen adlarını içerir. Dizi öğeleri 0 olabilir. Bir hata oluşursa, yeni bir `SAFEARRAY` döndürülmez.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre geçerli değil. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) yöntemi.

Siz niteleyicisi adları aldıktan sonra her niteleyicisi adına göre çağırarak erişebilirsiniz [QualifierSet_Get](qualifierset-get.md) işlevi.

Sıfır niteleyicileri olması belirli bir nesne için bir hata değil dizelerde sayısını `pstrNames` işlevi döndürür olsa bile getirisini 0 olabilir `WBEM_S_NO_ERROR`.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils.idl

**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)
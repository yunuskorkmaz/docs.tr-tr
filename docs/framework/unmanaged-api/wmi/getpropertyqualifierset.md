---
title: GetPropertyQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: GetPropertyQualifierSet işlevi, bir özelliğin niteleyici kümesini alır.
ms.date: 11/06/2017
api_name:
- GetPropertyQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyQualifierSet
helpviewer_keywords:
- GetPropertyQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4133145c7bea1fb3c018d809b9fea3de38270619
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127450"
---
# <a name="getpropertyqualifierset-function"></a>GetPropertyQualifierSet işlevi

Belirli bir özellik için niteleyici kümesini alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetPropertyQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszProperty,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszMethod`\
'ndaki Özellik adı. `wszProperty` geçerli bir `LPCWSTR`işaret etmelidir.

`ppQualSet`\
dışı Özelliğin niteleyicilerine erişim sağlayan arabirim işaretçisini alır. `ppQualSet` `null`olamaz. Bir hata oluşursa, yeni bir nesne döndürülmez ve işaretçi `null`işaret etmek üzere ayarlanır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen yöntem yok. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre `null`. |
| `WBEM_E_SYSTEM_PROPERTY` | 0x80041030 | İşlev bir sistem özelliğinin niteleyicilerini almaya çalışır. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetPropertyQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyqualifierset) yöntemine bir çağrı kaydırır.

Bu işleve yapılan çağrı yalnızca geçerli nesne bir CıM sınıf tanımınız ise desteklenir. CıM örneklerine işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri için yöntem düzenleme kullanılamaz.

Her yöntemin kendi niteleyicileri olabileceğinden, [IWbemQualifierSet işaretçisi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) çağıranın bu niteleyicileri eklemesini, düzenlemesini veya silmesine izin verir.

Sistem Özellikleri niteleyicisi olmadığından, bir sistem özelliği için bir [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) işaretçisi edinmeye çalışırsanız işlev `WBEM_E_SYSTEM_PROPERTY` döndürür.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

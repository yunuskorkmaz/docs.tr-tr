---
title: GetMethodQualifierSet işlevi (yönetilmeyen API Başvurusu)
description: GetMethodQualifierSet işlevi, bir yöntemin niteleyici kümesini alır.
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86a7788736c3c12cfcfd405de88dfadfb14c1eca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798533"
---
# <a name="getmethodqualifierset-function"></a>GetMethodQualifierSet işlevi

Belirli bir yöntem için niteleyici kümesini alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszMethod`\
'ndaki Yöntem adı. `wszMethod`geçerli `LPCWSTR`bir işaret etmelidir.

`ppQualSet`\
dışı Metodun niteleyicilerine erişime izin veren arabirim işaretçisini alır. `ppQualSet``null`olamaz. Bir hata oluşursa, yeni bir nesne döndürülmez ve işaretçi öğesine `null`işaret etmek üzere ayarlanır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen yöntem yok. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir parametre `null`. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) yöntemine bir çağrı kaydırır.

Bu işleve yapılan çağrı yalnızca geçerli nesne bir CıM sınıf tanımınız ise desteklenir. CıM örneklerine işaret eden [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçileri için yöntem düzenleme kullanılamaz.

Her yöntemin kendi niteleyicileri olabileceğinden, [IWbemQualifierSet işaretçisi](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) çağıranın bu niteleyicileri eklemesini, düzenlemesini veya silmesine izin verir.

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

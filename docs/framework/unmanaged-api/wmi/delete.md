---
title: Delete işlevi (yönetilmeyen API Başvurusu)
description: Delete işlevi, belirtilen özelliği ve tüm niteleyicileri bir CıM sınıf tanımından siler.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6b8f287be831702dd31a8335f9b2f6447bcee540
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127661"
---
# <a name="delete-function"></a>Delete işlevi

Belirtilen özelliği ve tüm niteleyicileri bir CıM sınıf tanımından siler.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszName`\
'ndaki Silinecek özelliğin adı. `wszName` geçerli bir `LPCWSTR`işaretçisi olmalıdır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Belirtilmeyen bir hata oluştu. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Özellik silinemiyor. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` geçersizdir. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik yok. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamaya yetecek bellek yok. |
| `WBEM_E_PROPAGATED_PROPERTY` | 0x8004101c | Özelliği bir temel sınıftan devralınır. |
| `WBEM_E_SYSTEM_PROPERTY` | | Özelliği bir sistem özelliğidir. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_E_RESET_TO_DEFAULT` | 0x80041030 | İşlev geçerli sınıf için geçersiz kılma varsayılan değerini sildi. Üst sınıftaki bu özellik için varsayılan değer yeniden etkinleştirildi. |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject::D Sil](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) yöntemine bir çağrı kaydırır.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

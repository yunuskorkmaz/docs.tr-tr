---
title: GetMethod işlevi (yönetilmeyen API Başvurusu)
description: GetMethod işlevi bir yöntem hakkında bilgi alır.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 48986f5ff1cbbb45840ec1a059aa86711848d717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102585"
---
# <a name="getmethod-function"></a>GetMethod işlevi

Belirtilen yöntem hakkında bilgi alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszName`\
'ndaki Yöntem adı. Bu parametre `null` olamaz ve geçerli bir `LPCWSTR`işaret etmelidir.

`lFlags`\
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`ppInSignature`\
dışı Yöntemine yönelik parametreleri açıklayan bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğinin adresine yönelik bir işaretçi. Bu parametre `null`olarak ayarlandıysa yok sayılır.

`ppOutSignature`\
dışı Yönteme giden parametreleri açıklayan bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğinin adresine yönelik bir işaretçi. Bu parametre `null`olarak ayarlandıysa yok sayılır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik bulunamadı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemine bir çağrı kaydırır.

Yöntemin parametrelere sahip olmaması halinde, Windows Yönetimi [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçisini `null` olarak ayarlayabilir.

`ppInSignature` ve `ppOutSignature`, sistem sınıfı [_parametrelerinin](/windows/desktop/WmiSdk/--parameters)`IWbemClassObject` örneğindeki özellikler olarak sırasıyla gelen ve dışarı parametreleri anlatmaktadır. `ppInSignature` özellikler, `Param`*n*olarak adlandırılır; burada *n* , yöntem imzasında parametrenin konumudur (`Param1`, `Param2`, vb.). `ppOutSignature` özellikler de `Param`*n*olarak adlandırılır ve döndürülen değer `ReturnValue`olarak adlandırılır. Daha fazla bilgi ve örnek için bkz. [IWbemClassObject:: GetMethod metodu](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

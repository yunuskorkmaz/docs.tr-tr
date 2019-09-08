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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798573"
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
'ndaki Yöntem adı. Bu parametre geçerli olamaz `null` ve geçerli `LPCWSTR`bir işaret etmelidir.

`lFlags`\
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`ppInSignature`\
dışı Yöntemine yönelik parametreleri açıklayan bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğinin adresine yönelik bir işaretçi. Bu parametre, olarak `null`ayarlandıysa yok sayılır.

`ppOutSignature`\
dışı Yönteme giden parametreleri açıklayan bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğinin adresine yönelik bir işaretçi. Bu parametre, olarak `null`ayarlandıysa yok sayılır.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik bulunamadı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemine bir çağrı kaydırır.

Windows yönetimi, metotta parametre yoksa, [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçisini `null` ' a ayarlayabilir.

`IWbemClassObject` Ve `ppInSignature` '`ppOutSignature` de, bir sistem sınıfı [_parametreleri](/windows/desktop/WmiSdk/--parameters)örneğindeki özellikler olarak sırasıyla ve içinde ve dışarı parametreleri açıklama. `ppInSignature` İçindeki Özellikler *n*olarak adlandırılır `Param`; burada *n* , yöntem imzasında `Param1` `Param2`parametre konumudur (örneğin, vb.). İçindeki `ppOutSignature` özellikler de n olarak adlandırılır `Param`ve dönüş değeri olarak adlandırılır. `ReturnValue` Daha fazla bilgi ve örnek için bkz. [IWbemClassObject:: GetMethod metodu](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Gereksinimler

**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

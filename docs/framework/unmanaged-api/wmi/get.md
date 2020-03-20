---
title: İşlev alın (Yönetilmeyen API Başvurusu)
description: Get işlevi belirtilen özellik değerini alır.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174985"
---
# <a name="get-function"></a>Get işlevi

Varsa belirtilen özellik değerini alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Get (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
[içinde] Bu parametre kullanılmaz.

`ptr`\
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`wszName`\
[içinde] Mülkün adı.

`lFlags`\
[içinde] Saklı -dır. Bu parametre 0 olmalıdır.

`pVal`\
[çıkış] İşlev başarılı bir şekilde dönerse, `wszName` özelliğin değerini içerir. Bağımsız `pval` değişken, niteleyici için doğru tür ve değer atanır.

`pvtType`\
[çıkış] İşlev başarıyla dönerse, özellik türünü gösteren bir [CIM tipi sabit](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) içerir. Değeri de olabilir. `null`

`plFlavor`\
[çıkış] İşlev başarıyla dönerse, özelliğin kaynağı hakkında bilgi alır. Değeri, `null` *WbemCli.h* üstbilgi dosyasında tanımlanan aşağıdaki WBEM_FLAVOR_TYPE sabitlerden biri olabilir:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | Özellik standart bir sistem özelliğidir. |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | Bir sınıf için: Özellik üst sınıftan devralır. <br> Örneğin: Özellik, üst sınıftan devralınmış olsa da, örnek tarafından değiştirilmedi.  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | Bir sınıf için: Özellik türemiş sınıfa aittir. <br> Örneğin: Özellik örnek tarafından değiştirilir; diğer bir şekilde, bir değer sağlandı veya bir niteleyici eklendi veya değiştirildi. |

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir başarısızlık oldu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değildir. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik bulunamadı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak için yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |

## <a name="remarks"></a>Açıklamalar

Bu işlev [IWbemClassObject](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) bir çağrı sarar::Get yöntemi.

İşlev `Get` sistem özelliklerini de döndürebilir.

Bağımsız `pVal` değişken, niteleyici ve COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) işlevi için doğru tür ve değer atanır

## <a name="requirements"></a>Gereksinimler

 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).

 **Üstbilgi:** WMINet_Utils.idl

 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)

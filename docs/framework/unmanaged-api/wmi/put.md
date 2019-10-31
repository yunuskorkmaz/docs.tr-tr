---
title: Put işlevi (yönetilmeyen API Başvurusu)
description: Put işlevi, adlandırılmış bir özelliğe yeni bir değer atar.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f1bb8aa09a269e3b8fd23f393d63a275d308a77c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127397"
---
# <a name="put-function"></a>Put işlevi

Adlandırılmış bir özelliği yeni bir değere ayarlar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a>Parametreler

`vFunc`\
'ndaki Bu parametre kullanılmıyor.

`ptr`\
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszName`\
'ndaki Özelliğin adı. Bu parametre `null`olamaz.

`lFlags`\
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`pVal`\
'ndaki Yeni özellik değeri haline gelen geçerli bir `VARIANT` işaretçisi. `pVal` `null` veya `VT_NULL`türünde bir `VARIANT` gösteriyorsa, özelliği `null`olarak ayarlanır.

`vtType`\
'ndaki `pVal`tarafından işaret edilen `VARIANT` türü. Daha fazla bilgi için [açıklamalar](#remarks) bölümüne bakın.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Genel bir hata oluştu. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Bir veya daha fazla parametre geçerli değil. |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | Özellik türü tanınmıyor. Sınıf örnekleri oluşturulurken Bu değer döndürülür. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi gerçekleştirmek için yeterli bellek yok. |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | Örnekler için: `pVal`, özellik için yanlış türde bir `VARIANT` işaret ettiğini gösterir. <br/> Sınıf tanımları için: özellik üst sınıfta zaten var ve yeni COM türü eski COM türünden farklı. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu. |

## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) yöntemine bir çağrı kaydırır.

Bu işlev her zaman geçerli özellik değerinin üzerine yeni bir değer yazar. [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) bir sınıf tanımına işaret ediyorsa, `Put` özellik değerini oluşturur veya güncelleştirir. [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) bir CIM örneğine işaret ediyorsa, `Put` yalnızca özellik değerini güncelleştirir; `Put` bir özellik değeri oluşturamıyor.

`__CLASS` System özelliği yalnızca sınıf oluşturma sırasında yazılabilir, boş bırakılmayabilir. Diğer tüm sistem özellikleri salt okunurdur.

Bir Kullanıcı, alt çizgi ("_") ile başlayan veya biten adlara sahip özellikler oluşturamaz. Bu sistem sınıfları ve özellikleri için ayrılmıştır.

`Put` işlevi tarafından ayarlanan özellik üst sınıfta varsa, özellik türü üst sınıf türüyle eşleşmediği takdirde özelliğin varsayılan değeri değiştirilir. Özellik yoksa ve bir tür uyumsuzluğu değilse, özellik oluşturulur.

`vtType` parametresini yalnızca bir CıM sınıf tanımında yeni özellikler oluştururken ve `pVal` `null` veya `VT_NULL`türünde bir `VARIANT` işaret ediyorsa kullanın. Bu durumda `vType` parametresi, özelliğin CıM türünü belirtir. Her iki durumda da, `vtType` 0 olmalıdır. temel nesne bir örnek ise (`Val` `null`olsa bile), özelliğin türü düzeltildiği ve değiştirilemediğinden, `vtType` de 0 olmalıdır.

## <a name="example"></a>Örnek

Bir örnek için, bkz. [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) yöntemi.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** WMINet_Utils. IDL

**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

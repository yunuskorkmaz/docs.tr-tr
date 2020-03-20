---
title: NextMethod işlevi (Yönetilmeyen API Başvurusu)
description: NextMethod işlevi bir sonraki yöntemi numaralandırmada alır.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 36acd6135110a8865bd8efdda628c352c01b4f26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174933"
---
# <a name="nextmethod-function"></a>NextMethod fonksiyonu
[BeginMethodEnumeration](beginmethodenumeration.md)için bir çağrı ile başlayan bir numaralandırma sonraki yöntemi alır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[içinde] Bu parametre kullanılmaz.

`ptr`  
[içinde] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine işaretçi.

`lFlags`  
[içinde] Saklı -dır. Bu parametre 0 olmalıdır.

`pName`  
[çıkış] Aramadan önce `null` işaret eden bir işaretçi. İşlev döndüğünde, yöntem adını `BSTR` içeren yeni bir adres.

`ppSignatureIn`  
[çıkış] Yöntem için parametreleri `in` içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) için bir işaretçi alan bir işaretçi.

`ppSignatureOut`  
[çıkış] Yöntem için parametreleri `out` içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) için bir işaretçi alan bir işaretçi.

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler *WbemCli.h* üstbilgi dosyasında tanımlanır veya bunları kodunuzdaki sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Fonksiyon arayın. [`BeginEnumeration`](beginenumeration.md) |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada başka özellik yok. |
  
## <a name="remarks"></a>Açıklamalar

Bu [işlev, IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemine bir çağrı yıkıyor.

Arayan numaralandırma sırasını [BeginMethodEnumeration](beginmethodenumeration.md) işlevini çağırarak başlatır ve işlev dönene `WBEM_S_NO_MORE_DATA`kadar [NextMethod] işlevini çağırır. İsteğe bağlı olarak, arayan [EndMethodEnumeration](endmethodenumeration.md)çağırarak sırayı bitirir. Arayan, [endmethodenumeration'ı](endmethodenumeration.md) herhangi bir zamanda arayarak numaralandırmayı erken sonlandırabilir.

## <a name="example"></a>Örnek

C++ örneği için [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemine bakın.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** WMINet_Utils.idl  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve Performans Sayaçları (Yönetilmeyen API Başvurusu)](index.md)

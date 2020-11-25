---
title: NextMethod işlevi (yönetilmeyen API Başvurusu)
description: NextMethod işlevi bir Numaralandırmadaki sonraki yöntemi alır.
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
ms.openlocfilehash: a0466aee47b0a6142870640c78b43f49e221ac2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726775"
---
# <a name="nextmethod-function"></a>NextMethod işlevi

Bir sonraki yöntemi [Beginmethodenumeration](beginmethodenumeration.md)çağrısıyla başlayan bir Numaralandırmadaki alır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Söz dizimi  
  
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
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`lFlags`  
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`pName`  
dışı Çağrıdan önce işaret eden bir işaretçi `null` . İşlev döndüğünde, `BSTR` Yöntem adını içeren yeni bir adresi.

`ppSignatureIn`  
dışı Yöntemi için parametreleri içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) öğesine işaretçi alan bir işaretçi `in` .

`ppSignatureOut`  
dışı Yöntemi için parametreleri içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) öğesine işaretçi alan bir işaretçi `out` .

## <a name="return-value"></a>Döndürülen değer

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101D | İşleve bir çağrı yoktu [`BeginEnumeration`](beginenumeration.md) . |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada daha fazla özellik yok. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemine bir çağrı kaydırır.

Çağıran, [Beginmethodenumeration](beginmethodenumeration.md) işlevini çağırarak numaralandırma dizisini başlatır ve ardından işlev dönene kadar [NextMethod] işlevini çağırır `WBEM_S_NO_MORE_DATA` . İsteğe bağlı olarak, çağıran, [Endmethodenumeration](endmethodenumeration.md)' ı çağırarak sırayı sonlandırır. Çağıran, her zaman [Endmethodenumeration](endmethodenumeration.md) ' ı çağırarak numaralandırmayı erken sonlandıramayabilir.

## <a name="example"></a>Örnek

Bir C++ örneği için, bkz. [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemi.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

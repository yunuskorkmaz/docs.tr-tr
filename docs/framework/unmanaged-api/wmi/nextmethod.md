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
ms.openlocfilehash: 1c20fe5b4a081bd41f51365a36ab5f8f8cfb71ed
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127368"
---
# <a name="nextmethod-function"></a>NextMethod işlevi
Bir sonraki yöntemi [Beginmethodenumeration](beginmethodenumeration.md)çağrısıyla başlayan bir Numaralandırmadaki alır.  

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
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`lFlags`  
'ndaki Ayrılamadı. Bu parametre 0 olmalıdır.

`pName`  
dışı Çağrıdan önce `null` işaret eden bir işaretçi. İşlev döndüğünde, yöntem adını içeren yeni bir `BSTR` adresi. 

`ppSignatureIn`  
dışı Yöntemi için `in` parametrelerini içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) öğesine işaretçi alan bir işaretçi. 

`ppSignatureOut`  
dışı Yöntemi için `out` parametrelerini içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) öğesine işaretçi alan bir işaretçi. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101D | [`BeginEnumeration`](beginenumeration.md) işlevine hiçbir çağrı yoktu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada daha fazla özellik yok. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemine bir çağrı kaydırır.

Çağıran, [Beginmethodenumeration](beginmethodenumeration.md) işlevini çağırarak numaralandırma dizisini başlatır ve ardından işlev `WBEM_S_NO_MORE_DATA`döndürünceye kadar [NextMethod] işlevini çağırır. İsteğe bağlı olarak, çağıran, [Endmethodenumeration](endmethodenumeration.md)' ı çağırarak sırayı sonlandırır. Çağıran, her zaman [Endmethodenumeration](endmethodenumeration.md) ' ı çağırarak numaralandırmayı erken sonlandıramayabilir.

## <a name="example"></a>Örnek

Bir C++ örnek için, bkz. [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

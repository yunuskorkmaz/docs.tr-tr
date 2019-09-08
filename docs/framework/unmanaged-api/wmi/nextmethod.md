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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee743a4499824bea723043d5a2c7d57d7cbd7106
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798427"
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
dışı Çağrıdan `null` önce işaret eden bir işaretçi. İşlev döndüğünde, yöntem adını içeren yeni `BSTR` bir adresi. 

`ppSignatureIn`  
dışı Yöntemi için `in` parametreleri içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) öğesine işaretçi alan bir işaretçi. 

`ppSignatureOut`  
dışı Yöntemi için `out` parametreleri içeren bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) öğesine işaretçi alan bir işaretçi. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101D | [`BeginEnumeration`](beginenumeration.md) İşleve bir çağrı yoktu. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Numaralandırmada daha fazla özellik yok. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemine bir çağrı kaydırır.

Çağıran, [Beginmethodenumeration](beginmethodenumeration.md) işlevini çağırarak numaralandırma dizisini başlatır ve ardından işlev dönene `WBEM_S_NO_MORE_DATA`kadar [NextMethod] işlevini çağırır. İsteğe bağlı olarak, çağıran, [Endmethodenumeration](endmethodenumeration.md)' ı çağırarak sırayı sonlandırır. Çağıran, her zaman [Endmethodenumeration](endmethodenumeration.md) ' ı çağırarak numaralandırmayı erken sonlandıramayabilir.

## <a name="example"></a>Örnek

Bir C++ örnek için, bkz. [IWbemClassObject:: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

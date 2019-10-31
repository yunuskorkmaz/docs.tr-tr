---
title: Inhersfrom işlevi (yönetilmeyen API Başvurusu)
description: Inhersfrom işlevi bir sınıfın veya örneğin belirli bir üst sınıftan türeip türetilmediğini belirler.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6bda63377251e3a208dfb1620896535ccdf8ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127426"
---
# <a name="inheritsfrom-function"></a>Inhersfrom işlevi
Geçerli sınıfın veya örneğin belirtilen bir üst sınıftan türeip türetilmediğini belirler.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

`wszAncestor`  
'ndaki Sınıfın adı. `wszAncestor` geçerli bir `LPCWSTR`işaret etmelidir.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | Geçerli nesne `wszAncestor`devralır.  |
| `WBEM_S_FALSE` | 1\. | Geçerli nesne `wszAncestor`öğesinden almıyor. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor` `null`. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: ınhersfrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) yöntemine bir çağrı kaydırır.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

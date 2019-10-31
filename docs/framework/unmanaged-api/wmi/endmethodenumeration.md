---
title: EndMethodEnumeration işlevi (yönetilmeyen API Başvurusu)
description: EndMethodEnumeration işlevi bir yöntem numaralandırma sırasını sonlandırır.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 174cf76d4b0ddf07e67e02bff20a983dca08819a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132016"
---
# <a name="endmethodenumeration-function"></a>EndMethodEnumeration işlevi
[Beginmethodenumeration işlevi](beginmethodenumeration.md)çağrısıyla başlatılan bir numaralandırma dizisini sonlandırır.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
'ndaki Bu parametre kullanılmıyor.

`ptr`  
'ndaki [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneğine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerler, *Wbemcli. h* üstbilgi dosyasında tanımlanır veya bunları kodunuzda sabitler olarak tanımlayabilirsiniz:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | 0x8004101D | Bir iç hata oluştu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev, [IWbemClassObject:: EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) yöntemine bir çağrı kaydırır.

Çağıran, [Beginmethodenumeration işlevini](beginmethodenumeration.md)kullanarak numaralandırma sırasını başlatır ve ardından Yöntem `WBEM_S_NO_MORE_DATA`dönene kadar [NextMethod işlevini](nextmethod.md )çağırır. Çağıran, isteğe bağlı olarak `EndMethodEnumeration`çağırarak sırayı sonlandırır. Çağıran, herhangi bir zamanda `EndMethodEnumeration` çağırarak numaralandırmayı erken sonlandıramayabilir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils. IDL  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

---
title: GetMethod işlevi (yönetilmeyen API Başvurusu)
description: GetMethod işlevi bir yöntem hakkındaki bilgileri alır.
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
ms.openlocfilehash: 5a405c5e245558e6b8d1b389bfc143faae4550a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577600"
---
# <a name="getmethod-function"></a>GetMethod işlevi
Belirtilen yöntem hakkındaki bilgileri alır.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
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

`vFunc`  
[in] Bu parametre kullanılmaz.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) örneği.

`wszName`  
[in] Yöntem adı. Bu parametre olamaz `null` ve geçerli bir işaret etmelidir `LPCWSTR`.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`ppInSignature`   
[out] Adresine bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yönteme giriş paramteers açıklayan örneği. Bu ayarlanırsa, bu parametre yoksayılır `null`. 

`ppOutSignature`  
[out] Adresine bir işaretçi bir [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) yöntemin out Parametreleri açıklayan örneği. Bu ayarlanırsa, bu parametre yoksayılır `null`. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üst bilgi dosyası veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik bulunamadı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarılı oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev bir çağrı sarılır [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) yöntemi.

Windows Yönetim ayarlayabilirsiniz [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) işaretçisine `null` yöntemi hiçbir parametreleri varsa.

İçinde `ppInSignature` ve `ppOutSignature` iç ve dış parametrelerin, sırasıyla özellikleri olarak açıklayan bir `IWbemClassObject` sistem sınıfının örneğini [_upravit](/windows/desktop/WmiSdk/--parameters). Özelliklerinde `ppInsignature` adlandırılır `Param` *n*burada *n* parametresi yöntem imzası konumudur (gibi `Param1`, `Param2`vb..). Özelliklerinde `ppOutSignature` olarak da adlandırılır `Param` *n*, ve dönüş değeri olarak adlandırılan `ReturnValue`. Daha fazla bilgi ve örnek için bkz. [IWbemClassObject::GetMethod yöntemi](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

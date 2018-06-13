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
ms.openlocfilehash: 65b8cb74a028892a3494e818f2b523f75e8766a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460453"
---
# <a name="getmethod-function"></a>GetMethod işlevi
Belirtilen yöntem bilgilerini alır.

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
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`wszName`  
[in] Yöntem adı. Bu parametre olamaz `null` ve geçerli bir işaret etmelidir `LPCWSTR`.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`ppInSignature`   
[out] Adresine bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) yöntemine içinde paramteers açıklar örneği. Bu ayarı etkinse, bu parametre yoksayılır `null`. 

`ppOutSignature`  
[out] Adresine bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) yöntemine out Parametreleri açıklayan örneği. Bu ayarı etkinse, bu parametre yoksayılır `null`. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik bulunamadı. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | İşlemi tamamlamak yeterli bellek yok. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx) yöntemi.

Windows Yönetim ayarlayabilirsiniz [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) işaretçi `null` yöntemi hiçbir parametreleri varsa.

İçinde `ppInSignature` ve `ppOutSignature` ve out parametreleri, sırasıyla özellikleri olarak açıklayan bir `IWbemClassObject` sistem sınıfının örneği [_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx). Özelliklerinde `ppInsignature` adlandırıldığı **Param *** n*, burada *n* parametresi yöntem imzası konumdur (gibi `Param1`, `Param2`vb..). Özelliklerinde `ppOutSignature` olarak da adlandırılır **Param *** n*, ve dönüş değeri adlı **ReturnValue**. Daha fazla bilgi ve bir örnek için bkz: [IWbemClassObject::GetMethod yöntemi](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx).

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

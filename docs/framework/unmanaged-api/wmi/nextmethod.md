---
title: "NextMethod işlevi (yönetilmeyen API Başvurusu)"
description: "NextMethod işlevi numaralandırma sonraki yöntem alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: NextMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: NextMethod
helpviewer_keywords: NextMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9b14424bb914be3ba127670e1b6490f79854d6e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="nextmethod-function"></a>NextMethod işlevi
Sonraki yöntem çağrısı ile başlayan bir numaralandırmasını alır [BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) örneği.

`lFlags`  
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`pName`  
[out] İşaret eden bir işaretçi `null` çağrı önce. İşlevi döndüğünde, yeni bir adres `BSTR` yöntem adını içerir. 

`ppSignatureIn`  
[out] Bir işaretçi alır bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) içeren `in` yöntemi için parametreler. 

`ppSignatureOut`  
[out] Bir işaretçi alır bir işaretçi bir [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) içeren `out` yöntemi için parametreler. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Hiçbir çağrısına vardı [ `BeginEnumeration` ](beginenumeration.md) işlevi. |
| `WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Sabit listede daha fazla özellik yok. |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) yöntemi.

Arayan çağırarak numaralandırma sırası başlar [BeginMethodEnumeration](beginmethodenumeration.md) işlev ve işlev döndürünceye kadar [NextMethod] işlevi çağırır `WBEM_S_NO_MORE_DATA`. İsteğe bağlı olarak, çağıran çağırarak sırası tamamlandıktan [EndMethodEnumeration](endmethodenumeration.md). Arayan numaralandırması erken çağırarak sonlandırabilir [EndMethodEnumeration](endmethodenumeration.md) dilediğiniz zaman.

## <a name="example"></a>Örnek

C++ örnek için bkz: [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) yöntemi.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

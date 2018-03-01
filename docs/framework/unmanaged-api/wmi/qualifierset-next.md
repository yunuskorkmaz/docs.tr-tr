---
title: "QualifierSet_Next işlevi (yönetilmeyen API Başvurusu)"
description: "QualifierSet_Next işlevi numaralandırma sonraki niteleyicisinde alır."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 01a9c9d162039547849597aaa9c8a6fa38a31455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetnext-function"></a>QualifierSet_Next işlevi
Sonraki çağrı kullanmaya bir numaralandırma niteleyicisinde alır [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) işlevi.   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`   
[in] Bu parametre kullanılmıyor.

`ptr`   
[in] Bir işaretçi bir [IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx) örneği.

`lFlags`   
[in] Ayrılmış. Bu parametre 0 olmalıdır.

`pstrName`   
[out] Niteleyici adı. Varsa `null`, bu parametre, yoksayılan Aksi takdirde `pstrName` geçerli bir işaret etmelidir değil `BSTR` veya bellek sızıntısı oluşur. Null, işlevi her zaman yeni bir ayırır, `BSTR` zaman döndürür `WBEM_S_NO_ERROR`.

`pVal`   
[out] Başarılı olduğunda, Niteleyici değeri. İşlev başarısız olursa, `VARIANT` gösterdiği `pVal` değiştirilmez. Bu parametre ise `null`, parametre yoksayılır.

`plFlavor`   
[out] Niteleyici türü alan uzun bir işaretçi. Özellik bilgileri değil istenirse, bu parametre olabilir `null`. 

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_UNEXPECTED` | 0x8004101d | Arayan çağrılmayan [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md). |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Yeni bir numaralandırma başlatmak yeterli bellek yok. |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Daha fazla hiçbir niteleyicileri numaralandırmada bırakılır. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemQualifierSet::Next](https://msdn.microsoft.com/library/aa391870(v=vs.85).aspx) yöntemi.

Çağırmanız `QualifierSet_Next` dönüş işlevi kadar tüm niteleyicileri art arda Numaralandırılacak işlevi `WBEM_S_NO_MORE_DATA`. Numaralandırma erken sonlandırmak için çağrı [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) işlevi.

Numaralandırma sırasında döndürülen niteleyicileri sırası tanımlanmamıştır.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

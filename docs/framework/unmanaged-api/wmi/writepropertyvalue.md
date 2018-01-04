---
title: "WritePropertyValue işlevi (yönetilmeyen API Başvurusu)"
description: "WritePropertyValue işlevi bir özelliğe bayt yazar."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: WritePropertyValue
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: WritePropertyValue
helpviewer_keywords: WritePropertyValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7221c9e0f1cb49ab0e27130ce69c0527ba903148
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue işlevi
Bir özellik tanımlayıcısı tarafından tanımlanan bir özellik için belirtilen sayıda baytı yazar.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) örneği.

`lHandle`  
[in] Bu özelliği tanımlar tanıtıcı içeren bir tamsayı. Tanıtıcı çağırarak alınabilir [GetPropertyHandle](getpropertyhandle.md) işlevi.   

`lNumBytes`  
[in] Özelliğin yazılan bayt sayısı. Bkz: [açıklamalar](#remarks) daha fazla bilgi için bölüm.

`pHandle`   
[out] Verileri içeren bayt dizisi için bir işaretçi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Tür uyumsuzluğu oluştu. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) yöntemi.

Dize ve tüm diğer olmayan ayarlamak için bu işlevi kullanın`DWORD` olmayan veya -`QWORD` veri.

Dize olmayan özellik değerleri için `lNumBytes` belirtilen özellik türü doğru veri boyutu olmalıdır. Dize özellik değerleri için `lNumBytes` uzunluğu olmalıdır ve bayt cinsinden belirtilen dize, dize kendisi bayt bile bir uzunlukta olmalıdır ve null sonlandırma karakteri ile izlemelidir.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

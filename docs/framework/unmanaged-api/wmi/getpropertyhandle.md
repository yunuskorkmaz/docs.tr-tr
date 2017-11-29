---
title: "GetPropertyHandle işlevi (yönetilmeyen API Başvurusu)"
description: "GetPropertyHandle işlevi bu identies bir özelliği bir benzersiz tanıtıcı döndürür."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetPropertyHandle
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetPropertyHandle
helpviewer_keywords: GetPropertyHandle function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ab3df6d2233059de76036da7ff27f5cc1808aaf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="getpropertyhandle-function"></a>GetPropertyHandle işlevi
Bir özelliği tanımlayan benzersiz bir tanıtıcı döndürür.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a>Parametreler

`vFunc`  
[in] Bu parametre kullanılmıyor.

`ptr`  
[in] Bir işaretçi bir [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) örneği.

`wszPropertyName`  
[in] Özellik adını içeren UTF16 kodlu characaters null ile sonlandırılmış dizisi.   

`pType`  
[out] Bir işaretçi bir [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) özelliğinin CIM türünü temsil eden numaralandırma üyesi.

`pHandle`   
[out] Özellik işleyicisi içeren bir tamsayı gösteren bir işaretçi.

## <a name="return-value"></a>Dönüş değeri

Bu işlev tarafından döndürülen aşağıdaki değerleri tanımlanan *WbemCli.h* üstbilgi dosyası, veya tanımlayabilirsiniz bunları sabitleri kodunuzda:

|Sabit  |Değer  |Açıklama  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Belirtilen özellik adı bulunamadı. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametre geçerli değil. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | İstenen özellik türünde olan `CIM_OBJECT` veya `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | İşlev çağrısı başarısız oldu.  |
  
## <a name="remarks"></a>Açıklamalar

Bu işlev çağrısı sarmalar [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) yöntemi.

Bu işleyici kullanırken özelliklerini tanımlamak için kullanabileceğiniz [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) özellik değerlerini okumak veya yazmak için yöntem.

Tanıtıcıları alınabilir tüm veri türlerinin özelliklerini dışında `CIM_OBJECT` ve `CIM_ARRAY`. İşler iş bir sınıfın tüm örneklerini döndürdü.

## <a name="requirements"></a>Gereksinimler  
**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** WMINet_Utils.idl  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
[WMI ve performans sayaçları (yönetilmeyen API Başvurusu)](index.md)

---
title: "COR_TYPEID Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPEID
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPEID
helpviewer_keywords: COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 795dea77ac8dac1e1d22574c23f1e1c13344a71a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cortypeid-structure"></a>COR_TYPEID Yapısı
Tür tanımlayıcısı içeriyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`token1`|İlk belirteci.|  
|`token2`|İkinci belirteci.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_TYPEID` Yapısı çeşitli atık olarak toplanmış olacak nesneleri hakkında bilgi sağlayan hata ayıklama yöntemler tarafından döndürülür. Bunun ardından bağımsız değişken olarak bu öğe hakkında ek bilgiler sağlayan diğer hata ayıklama yöntemlerine geçirilebilir. Örneğin, numaralandırma tarafından bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) nesnesi, tek tek alabilir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında ayrı ayrı nesneleri temsil eden nesne. Ardından geçirebilirsiniz `COR_TYPEID` değeri `COR_HEAPOBJECT.type` alanı [Icordebugprocess5::gettypefortypeıd](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) nesne türü bilgilerini sağlayan bir Icordebugtype nesne alma yöntemi.  
  
 A `COR_TYPEID` nesne donuk olacak şekilde tasarlanmıştır. Tek tek alanların erişilen veya değil. Bunun tek olarak sağlanan bir tanımlayıcı olarak kullanılır bir `out` yöntem çağrısı ve o can parametresinde sırayla, ek bilgi sağlamak için diğer yöntemleri için geçirilen.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

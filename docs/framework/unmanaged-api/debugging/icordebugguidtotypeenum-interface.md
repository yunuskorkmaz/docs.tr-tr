---
title: ICorDebugGuidToTypeEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum
helpviewer_keywords: ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e419c61d2918a1f17c0739c9782472f25dfe8cfa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum Arabirimi
Icordebugtype örnekleri tarafından temsil edilen bunların karşılık gelen türlerine ve GUID'ler kümesi arasında eşleme tanımlayan bir numaralandırıcı sağlar. Bu arabirim yöntemleri Icordebugenum arabiriminden devralır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Icordebugguidtotypeenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|Belirtilen sayıda alır [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) bilgilerini yazmak için GUID'leri eşleme örnekleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugGuidToTypeEnum` arabirimi nesnesi çağırarak alınabilir [Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi. Bir hata ayıklayıcısı bu arabirimin çağırabilirsiniz [sonraki](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) alma yöntemi [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) eşleşmelerini temsil eden nesneler yönetilen gösterimlerini [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri yüklendi uygulama etki alanı çağrısı için kullanılan [Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

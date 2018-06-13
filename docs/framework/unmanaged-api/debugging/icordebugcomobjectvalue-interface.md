---
title: ICorDebugComObjectValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11afee9c2a84999ccad2cdc12e2a14a4dc17d542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412532"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue Arabirimi
Bir çalışma zamanı aranabilir sarmalayıcısı (RCW) ile ilgili bilgileri almak için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCachedInterfacePointers Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Üzerinde geçerli RCW önbelleğe ham arabirim işaretçileri alır.|  
|[GetCachedInterfaceTypes Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Bir numaralandırıcı arabirimi türleri için geçerli nesne için ortası veya bırakıldığı olarak kullanılan olmasını sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 "ICorDebugValue" arabiriminin bir örneği bir RCW temsil edip etmediğini denetlemek için bir hata ayıklayıcısı çağırır `QueryInterface` ile "Icordebugvalue" üzerinde `IID_ICorDebugComObjectValue`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugProcess2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3009ee6a2ba22771a2132032744f76ca527c422
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965689"
---
# <a name="icordebugprocess2-interface"></a>ICorDebugProcess2 Arabirimi
Temsil eden bir işlem çalışan yönetilen kod Icordebugprocess arabirimi öğesinin mantıksal uzantısı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ClearUnmanagedBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|Belirtilen uzaklık daha önceki bir çağrı tarafından ayarlanan bir kesme noktasında kaldırır `ICorDebugProcess2::SetUnmanagedBreakpoint`.|  
|[GetDesiredNGENCompilerFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|Bu tarafından başvurulan işlemine görüntüyü yüklemek için ortak dil çalışma zamanı Modülü (CLR) ayarlanmalıdır bayrakları alır `ICorDebugProcess2`.|  
|[GetReferenceValueFromGCHandle Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|Bir başvuru işaretçi, tanıtıcı bir çöp toplama olan belirtilen yönetilen nesneyi alır.|  
|[GetThreadForTaskID Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|Bağlı belirtilen tanımlayıcıya sahip bir görevi yürüten iş parçacığının alır.|  
|[GetVersion Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|Ayıklanan işlemin çalıştığı CLR sürümünü alır.|  
|[SetDesiredNGENCompilerFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|Just-ın-time (JIT) derleyicinin ayıklanan işleme görüntüyü yüklemek için gerekli olan bayraklarını ayarlar.|  
|[SetUnmanagedBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

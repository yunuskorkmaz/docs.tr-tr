---
title: ICorDebugEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: 7575be3f5074243b251c80b8dd5bdbb12e5d50fd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976336"
---
# <a name="icordebugenum-interface"></a>ICorDebugEnum Arabirimi

Bir hata ayıklama uygulaması tarafından kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icordebugenum-clone-method.md)|Bu `ICorDebugEnum` nesnenin bir kopyasını oluşturur.|  
|[GetCount Yöntemi](icordebugenum-getcount-method.md)|Numaralandırmadaki öğelerin sayısını alır.|  
|[Reset Yöntemi](icordebugenum-reset-method.md)|İmleci numaralandırmanın başlangıcına kaydırır.|  
|[Skip Yöntemi](icordebugenum-skip-method.md)|İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki Numaralandırıcılar öğesinden `ICorDebugEnum`türetilir:  
  
- ICorDebugAppDomainEnum  
  
- ICorDebugAssemblyEnum  
  
- [ICorDebugBlockingObjectEnum](icordebugblockingobjectenum-interface.md)  
  
- ICorDebugBreakpointEnum  
  
- ICorDebugChainEnum  
  
- ICorDebugCodeEnum  
  
- ICorDebugErrorInfoEnum  
  
- [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md)  
  
- ICorDebugFrameEnum  
  
- [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md)  
  
- [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)  
  
- [ICorDebugHeapEnum](icordebugheapenum-interface.md)  
  
- [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)  
  
- ICorDebugModuleEnum  
  
- ICorDebugObjectEnum  
  
- ICorDebugProcessEnum  
  
- ICorDebugStepperEnum  
  
- ICorDebugThreadEnum  
  
- ICorDebugTypeEnum  
  
- ICorDebugValueEnum  
  
- [Icordebugvariablehomeenum](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

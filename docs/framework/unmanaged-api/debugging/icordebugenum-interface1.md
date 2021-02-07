---
description: 'Bu konuda daha fazla bilgi edinin: ıcorı, Genum arabirimi'
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
ms.openlocfilehash: 20d2bb14bddcaf40802567ec78a8e318ac1db380
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694480"
---
# <a name="icordebugenum-interface"></a>ICorDebugEnum Arabirimi

Bir hata ayıklama uygulaması tarafından kullanılan numaralandırıcıların soyut temel arabirimi olarak görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icordebugenum-clone-method.md)|Bu nesnenin bir kopyasını oluşturur `ICorDebugEnum` .|  
|[GetCount Yöntemi](icordebugenum-getcount-method.md)|Numaralandırmadaki öğelerin sayısını alır.|  
|[Reset Yöntemi](icordebugenum-reset-method.md)|İmleci numaralandırmanın başlangıcına kaydırır.|  
|[Skip Yöntemi](icordebugenum-skip-method.md)|İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Aşağıdaki Numaralandırıcılar öğesinden türetilir `ICorDebugEnum` :  
  
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

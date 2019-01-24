---
title: Icordebugenum arabirimi1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97080f7d850e67d635f9a65ee85ad3ddddbb244d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732758"
---
# <a name="icordebugenum-interface1"></a>Icordebugenum arabirimi1
Hata ayıklama bir uygulama tarafından kullanılan numaralandırıcılar için soyut temel arayüz görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|Bu bir kopyasını oluşturur `ICorDebugEnum` nesne.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|Sabit listede öğe sayısını alır.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|İmleç numaralandırma başlangıcına taşır.|  
|[Skip Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|İmleci İleri numaralandırmada tarafından belirtilen sayıda öğeyi taşır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki numaralandırıcılar türetilmesi `ICorDebugEnum`:  
  
-   "ICorDebugAppDomainEnum"  
  
-   "ICorDebugAssemblyEnum"  
  
-   [Icordebugblockingobjectenum](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   "ICorDebugBreakpointEnum"  
  
-   "ICorDebugChainEnum"  
  
-   "ICorDebugCodeEnum"  
  
-   "Icordebugerrorınfoenum"  
  
-   [Icordebugexceptionobjectcallstackenum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   "ICorDebugFrameEnum"  
  
-   [Icordebuggcreferenceenum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [Icordebugguidtotypeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [Icordebugheapsegmentenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   "ICorDebugModuleEnum"  
  
-   "ICorDebugObjectEnum"  
  
-   "ICorDebugProcessEnum"  
  
-   "ICorDebugStepperEnum"  
  
-   "ICorDebugThreadEnum"  
  
-   "ICorDebugTypeEnum"  
  
-   "ICorDebugValueEnum"  
  
-   [Icordebugvariablehomeenum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

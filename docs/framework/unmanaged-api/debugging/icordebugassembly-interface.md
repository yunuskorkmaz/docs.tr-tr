---
title: Icordebugassembly Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly
helpviewer_keywords: ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6331c00c2be0805afb56028e9e1a13cd11168cf1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly-interface1"></a>Icordebugassembly Interface1
Bir derlemeyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateModules Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Derlemesinde bulunan modülleri için bir numaralandırıcı alır.|  
|[GetAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Bu içeren uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugAssembly` örneği.|  
|[GetCodeBase Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|.NET Framework'ün geçerli sürümde uygulanmadı.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Derlemenin adını alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Derleme çalıştığı Icordebugprocess örneğini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

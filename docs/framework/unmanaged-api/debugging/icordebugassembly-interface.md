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
ms.openlocfilehash: d08bb1d2bb7adcbdeb49cd634755d243d34d7f84
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassembly-interface1"></a>Icordebugassembly Interface1
Bir derlemeyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateModules yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Derlemesinde bulunan modülleri için bir numaralandırıcı alır.|  
|[GetAppDomain yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Bu içeren uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugAssembly` örneği.|  
|[GetCodeBase yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|.NET Framework'ün geçerli sürümde uygulanmadı.|  
|[GetName yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Derlemenin adını alır.|  
|[GetProcess yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Derleme çalıştığı Icordebugprocess örneğini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugAssembly Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b802845e36e818a962484c1fea09cbcc1ceefd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974581"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly Arabirimi

Bir derlemeyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateModules Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Derlemesinde bulunan modüller için bir numaralandırıcı alır.|  
|[GetAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Bu içeren uygulama etki alanı için bir arabirim işaretçisi alır `ICorDebugAssembly` örneği.|  
|[GetCodeBase Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|.NET Framework'ün geçerli sürümde uygulanmadı.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Derlemenin adını alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Derleme çalıştığı Icordebugprocess örneğini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

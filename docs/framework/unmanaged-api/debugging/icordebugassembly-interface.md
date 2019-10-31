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
ms.openlocfilehash: dea3231e3bbb361b56254756c6d99b115f73e792
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133964"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly Arabirimi

Bir derlemeyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateModules Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Derlemede bulunan modüller için bir Numaralandırıcı alır.|  
|[GetAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Bu `ICorDebugAssembly` örneğini içeren uygulama etki alanına bir arabirim işaretçisi alır.|  
|[GetCodeBase Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|.NET Framework geçerli sürümünde uygulanmadı.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Derlemenin adını alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Derlemenin çalıştığı ICorDebugProcess örneğini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

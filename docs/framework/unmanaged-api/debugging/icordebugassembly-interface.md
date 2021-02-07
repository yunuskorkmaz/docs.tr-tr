---
description: ': ICorDebugAssembly arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 746b5f4b2f26550788708d93bf0dd50f5f495041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711953"
---
# <a name="icordebugassembly-interface"></a>ICorDebugAssembly Arabirimi

Bir derlemeyi temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateModules Yöntemi](icordebugassembly-enumeratemodules-method.md)|Derlemede bulunan modüller için bir Numaralandırıcı alır.|  
|[GetAppDomain Yöntemi](icordebugassembly-getappdomain-method.md)|Bu örneği içeren uygulama etki alanına bir arabirim işaretçisi alır `ICorDebugAssembly` .|  
|[GetCodeBase Yöntemi](icordebugassembly-getcodebase-method.md)|.NET Framework geçerli sürümünde uygulanmadı.|  
|[GetName Yöntemi](icordebugassembly-getname-method.md)|Derlemenin adını alır.|  
|[GetProcess Yöntemi](icordebugassembly-getprocess-method.md)|Derlemenin çalıştığı ICorDebugProcess örneğini alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

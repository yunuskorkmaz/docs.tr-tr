---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugmoduledebugger gevent arabirimi'
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: 0c2d43d7b04caeea0407ede23f0df6e278d60c92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801039"
---
# <a name="icordebugmoduledebugevent-interface"></a>ICorDebugModuleDebugEvent Arabirimi

Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetModule Yöntemi](icordebugmoduledebugevent-getmodule-method.md)|Yeni yüklenen veya kaldırılan birleştirilmiş modülü alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygular.  
  
> [!NOTE]
> Arabirim yalnızca .NET Native kullanılabilir. `QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)

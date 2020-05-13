---
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: ec6bad730d807b9a36ce5bba1c6f5d80da375f6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213339"
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

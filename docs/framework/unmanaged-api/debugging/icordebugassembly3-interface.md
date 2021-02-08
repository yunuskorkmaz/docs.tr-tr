---
description: 'Daha fazla bilgi edinin: ICorDebugAssembly3 Interface'
title: ICorDebugAssembly3 Arabirimi
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 3a8cabf41dffa75d82c2b6fde53dff2ede4838e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791510"
---
# <a name="icordebugassembly3-interface"></a>ICorDebugAssembly3 Arabirimi

Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere ICorDebugAssembly arabirimini mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateContainedAssemblies Yöntemi](icordebugassembly3-enumeratecontainedassemblies-method.md)|Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.|  
|[GetContainerAssembly Yöntemi](icordebugassembly3-getcontainerassembly-method.md)|Bu nesnenin kapsayıcı derlemesini döndürür `ICorDebugAssembly3` .|  
  
## <a name="remarks"></a>Açıklamalar  
  
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

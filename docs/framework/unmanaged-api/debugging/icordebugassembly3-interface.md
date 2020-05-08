---
title: ICorDebugAssembly3 Arabirimi
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 67707092c80b0e07aa284336c426aba09ff991af
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894823"
---
# <a name="icordebugassembly3-interface"></a>ICorDebugAssembly3 Arabirimi
Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere ICorDebugAssembly arabirimini mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateContainedAssemblies Yöntemi](icordebugassembly3-enumeratecontainedassemblies-method.md)|Bu derlemede yer alan derlemeler için bir Numaralandırıcı alır.|  
|[GetContainerAssembly Yöntemi](icordebugassembly3-getcontainerassembly-method.md)|Bu `ICorDebugAssembly3` nesnenin kapsayıcı derlemesini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Arabirim yalnızca .NET Native kullanılabilir. .NET Native dışında ICorDebug senaryolarına `QueryInterface` `E_NOINTERFACE` yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)

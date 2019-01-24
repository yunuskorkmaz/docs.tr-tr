---
title: ICorDebugAssembly3 Arabirimi
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66d3024c0bb2c0014cbec2b24deb7b0d5845fe88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627531"
---
# <a name="icordebugassembly3-interface"></a>ICorDebugAssembly3 Arabirimi
Icordebugassembly arabirimi kapsayıcı derlemeleri ve bunların içerdiği derlemeleri için destek sağlamak için mantıksal olarak genişletir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateContainedAssemblies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|Bu derlemede bulunan derlemeler için bir numaralandırıcı alır.|  
|[GetContainerAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|Bu kapsayıcı derleme döndürür `ICorDebugAssembly3` nesne.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Arabirimi yalnızca .NET Native ile kullanılabilir. Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

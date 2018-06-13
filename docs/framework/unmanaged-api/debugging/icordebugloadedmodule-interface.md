---
title: ICorDebugLoadedModule Arabirimi
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07d6dcc1873e24f84f97c877e8198c27eceef0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420797"
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule Arabirimi
Yüklenen modülü hakkında bilgi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBaseAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|Yüklenen modülün taban adresi alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|Yüklenen modül adını alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|Yüklenen modülün bayt cinsinden boyutu alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugLoadedModule` Arabirimi bir hata ayıklayıcı tarafından uygulanır ve hata ayıklama arabirimleri CLR tarafından hata ayıklayıcı'dan yüklenen modülü hakkında bilgi almak için kullanılır.  
  
> [!NOTE]
>  Bu arabirim yalnızca .NET yerel ile kullanılabilir. Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

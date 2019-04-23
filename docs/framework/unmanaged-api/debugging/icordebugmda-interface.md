---
title: ICorDebugMDA Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098675"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA Arabirimi
Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDescription Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Bu mda'nın bir açıklamasını içeren bir dize alır.|  
|[GetFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|İle bu mda'nın ilişkili bayraklar alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Bu mda'nın adını içeren bir dize alır.|  
|[GetOSThreadId Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Bu MDA, üzerinde yürütülmekte olan işletim sistemi iş parçacığı tanımlayıcısını alır.|  
|[GetXML Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|İle bu mda'nın ilişkili tam XML akışı alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

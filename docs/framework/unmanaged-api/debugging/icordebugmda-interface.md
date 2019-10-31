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
ms.openlocfilehash: 4201fe23bf54388510088e21471edce91809e94c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129795"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA Arabirimi
Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDescription Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Bu MDA 'ın açıklamasını içeren bir dize alır.|  
|[GetFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Bu MDA ile ilişkili bayrakları alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Bu MDA 'ın adını içeren bir dize alır.|  
|[GetOSThreadId Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Bu MDA 'ın üzerinde yürütüldüğü işletim sistemi iş parçacığı tanımlayıcısını alır.|  
|[GetXML Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Bu MDA ile ilişkili tam XML akışını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

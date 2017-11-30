---
title: ICorDebugMDA Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA
helpviewer_keywords: ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 00a003ee060de59fe0eb8ce8f740a620d77a7c85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA Arabirimi
Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetDescription yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Bu MDA açıklamasını içeren bir dize alır.|  
|[GetFlags yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Bu MDA ile ilişkili bayraklar alır.|  
|[GetName yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Bu MDA adını içeren bir dize alır.|  
|[Getosthreadıd yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Bu MDA dosyanızın çalıştığı işletim sistemi iş parçacığı tanımlayıcısını alır.|  
|[GetXML yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Bu MDA ile ilişkili tam XML akışı alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

---
title: Icordebugappdomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain
helpviewer_keywords: ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19cf38920ed818dfbba9cd83bd64fdc408281e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain-interface1"></a>Icordebugappdomain Interface1
Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar. Bu arabirim Icordebugcontroller sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Attach yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Hata ayıklayıcı uygulama etki alanına ekler.|  
|[EnumerateAssemblies yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Bir numaralandırıcı derlemeler için uygulama etki alanında alır.|  
|[EnumerateBreakpoints yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Bir numaralandırıcı uygulama etki alanı için tüm etkin kesme noktalarını alır.|  
|[EnumerateSteppers yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Bir numaralandırıcı uygulama etki alanı için tüm etkin adımlayıcıların alır.|  
|[GetID yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Uygulama etki alanı benzersiz Kimliğini alır.|  
|[Getmodulefrommetadataınterface yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Belirtilen meta veriler arabirimi Icordebugmodule nesnesini alır.|  
|[GetName yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Uygulama etki alanı adını alır.|  
|[GetObject yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Ortak dil çalışma zamanı (CLR) uygulama etki alanı için bir arabirim işaretçisi alır.|  
|[GetProcess yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Uygulama etki alanını içeren işlem alır.|  
|[Isattached yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

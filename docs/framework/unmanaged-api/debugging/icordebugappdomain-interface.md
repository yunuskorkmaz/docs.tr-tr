---
title: Icordebugappdomain Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84a11b6264ac0e241c1975eea5626edbdddce206
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain-interface1"></a>Icordebugappdomain Interface1
Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar. Bu arabirim Icordebugcontroller sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Attach Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Hata ayıklayıcı uygulama etki alanına ekler.|  
|[EnumerateAssemblies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Bir numaralandırıcı derlemeler için uygulama etki alanında alır.|  
|[EnumerateBreakpoints Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Bir numaralandırıcı uygulama etki alanı için tüm etkin kesme noktalarını alır.|  
|[EnumerateSteppers Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Bir numaralandırıcı uygulama etki alanı için tüm etkin adımlayıcıların alır.|  
|[GetId Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Uygulama etki alanı benzersiz Kimliğini alır.|  
|[GetModuleFromMetaDataInterface Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Belirtilen meta veriler arabirimi Icordebugmodule nesnesini alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Uygulama etki alanı adını alır.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Ortak dil çalışma zamanı (CLR) uygulama etki alanı için bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Uygulama etki alanını içeren işlem alır.|  
|[IsAttached Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

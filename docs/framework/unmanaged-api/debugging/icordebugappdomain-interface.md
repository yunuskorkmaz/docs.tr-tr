---
title: ICorDebugAppDomain Arabirimi
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
ms.openlocfilehash: 12753ab65f9339e8f6c3049bb72755e87464eb1a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963104"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain Arabirimi

Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar. Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Attach Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Hata ayıklayıcıyı uygulama etki alanına iliştirir.|  
|[EnumerateAssemblies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Uygulama etki alanındaki derlemeler için bir Numaralandırıcı alır.|  
|[EnumerateBreakpoints Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Uygulama etki alanındaki tüm etkin kesme noktaları için bir Numaralandırıcı alır.|  
|[EnumerateSteppers Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Uygulama etki alanındaki tüm etkin stepdenetleyicileri için bir Numaralandırıcı alır.|  
|[GetId Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Uygulama etki alanının benzersiz KIMLIĞINI alır.|  
|[GetModuleFromMetaDataInterface Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Belirtilen meta veri arabirimiyle ICorDebugModule nesnesini alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Uygulama etki alanının adını alır.|  
|[GetObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Uygulama etki alanını içeren işlemi alır.|  
|[IsAttached Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Hata ayıklayıcının uygulama etki alanına eklenip eklenmeyeceğini belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.openlocfilehash: 140e67417f4fad552f972a93bc8c620b440b2370
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895168"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain Arabirimi

Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar. Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Attach Yöntemi](icordebugappdomain-attach-method.md)|Hata ayıklayıcıyı uygulama etki alanına iliştirir.|  
|[EnumerateAssemblies Yöntemi](icordebugappdomain-enumerateassemblies-method.md)|Uygulama etki alanındaki derlemeler için bir Numaralandırıcı alır.|  
|[EnumerateBreakpoints Yöntemi](icordebugappdomain-enumeratebreakpoints-method.md)|Uygulama etki alanındaki tüm etkin kesme noktaları için bir Numaralandırıcı alır.|  
|[EnumerateSteppers Yöntemi](icordebugappdomain-enumeratesteppers-method.md)|Uygulama etki alanındaki tüm etkin stepdenetleyicileri için bir Numaralandırıcı alır.|  
|[GetID Yöntemi](icordebugappdomain-getid-method.md)|Uygulama etki alanının benzersiz KIMLIĞINI alır.|  
|[GetModuleFromMetaDataInterface Yöntemi](icordebugappdomain-getmodulefrommetadatainterface-method.md)|Belirtilen meta veri arabirimiyle ICorDebugModule nesnesini alır.|  
|[GetName Yöntemi](icordebugappdomain-getname-method.md)|Uygulama etki alanının adını alır.|  
|[GetObject Metodu](icordebugappdomain-getobject-method.md)|Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](icordebugappdomain-getprocess-method.md)|Uygulama etki alanını içeren işlemi alır.|  
|[IsAttached Yöntemi](icordebugappdomain-isattached-method.md)|Hata ayıklayıcının uygulama etki alanına eklenip eklenmeyeceğini belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

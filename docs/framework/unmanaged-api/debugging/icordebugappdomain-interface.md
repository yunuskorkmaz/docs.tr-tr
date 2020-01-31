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
ms.openlocfilehash: da7c0fb472df89d94fa702a13eff968a4c7e68e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785037"
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
|[GetId Yöntemi](icordebugappdomain-getid-method.md)|Uygulama etki alanının benzersiz KIMLIĞINI alır.|  
|[GetModuleFromMetaDataInterface Yöntemi](icordebugappdomain-getmodulefrommetadatainterface-method.md)|Belirtilen meta veri arabirimiyle ICorDebugModule nesnesini alır.|  
|[GetName Yöntemi](icordebugappdomain-getname-method.md)|Uygulama etki alanının adını alır.|  
|[GetObject Yöntemi](icordebugappdomain-getobject-method.md)|Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.|  
|[GetProcess Yöntemi](icordebugappdomain-getprocess-method.md)|Uygulama etki alanını içeren işlemi alır.|  
|[IsAttached Yöntemi](icordebugappdomain-isattached-method.md)|Hata ayıklayıcının uygulama etki alanına eklenip eklenmeyeceğini belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

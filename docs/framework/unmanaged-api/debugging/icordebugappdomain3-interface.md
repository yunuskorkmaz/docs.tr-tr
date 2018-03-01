---
title: ICorDebugAppDomain3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 017a2f018569b17c0b0011638e16f1921b6c9801
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 Arabirimi
Yönetilen gösterimlerini hakkında bilgi almak için yöntemleri sağlar [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri bir uygulama etki alanında şu anda yüklü. Bu arabirim, Icordebugappdomain ve Icordebugappdomain2 arabirimleri uzantısıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Tüm önbelleğe alınmış bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] türleri.|  
|[Icordebugappdomain3::getcachedwinrttypesforııds](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Önbelleğe alınan için bir numaralandırıcı alır [!INCLUDE[wrt](../../../../includes/wrt-md.md)] kendi arabirim tanımlayıcıları temel alarak bir uygulama etki alanındaki tür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim tarafından bir hata ayıklayıcısı işlevi değerlendirme çağrısı ile birlikte kullanılmak üzere tasarlanmıştır `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Ne zaman yöntemi alır tarafından desteklenen arabirim tanımlayıcıları bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] sunucu nesnesi, hata ayıklayıcı bu arabirimleri karşılık yönetilen türler eşleştirmek için bu arabiriminde tanımlanan yöntemleri kullanabilir.  
  
 Bu arabirim örneğini almak üzere çalışmaya `QueryInterface` Icordebugappdomain veya Icordebugappdomain2 arabirimi örneği üzerinde.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugAppDomain3 Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c130b92fd5114d067730da3b7cd138d98cf0577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 **Platform:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

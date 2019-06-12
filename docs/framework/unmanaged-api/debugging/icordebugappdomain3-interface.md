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
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025887"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 Arabirimi
Windows çalışma zamanı türleri bir uygulama etki alanında şu anda yüklü yönetilen gösterimleri hakkında bilgi almak için yöntemler sağlar. Bu arabirim, Icordebugappdomain ve Icordebugappdomain2 arabirimlerinin bir uzantısıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Önbelleğe alınan tüm Windows çalışma zamanı türleri için bir numaralandırıcı alır.|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Bir numaralandırıcı, kendi arabirimi tanımlayıcılarına göre bir uygulama etki alanındaki önbelleğe alınmış Windows çalışma zamanı türleri için alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim tarafından bir hata ayıklayıcı bir işlev değerlendirmesi çağrısı ile birlikte kullanılmak üzere tasarlanmıştır `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Yöntemi bir Windows çalışma zamanı sunucu nesnesi tarafından desteklenen arabirim tanımlayıcıları aldığında, hata ayıklayıcı Bu arabirimler için karşılık gelen yönetilen türler eşlemek için bu arabirimde tanımlanan yöntemler kullanabilir.  
  
 Bu arabirim örneğini almak için çalıştırın `QueryInterface` Icordebugappdomain veya Icordebugappdomain2 arabirimi örneği üzerinde.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Windows Çalışma Zamanı  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

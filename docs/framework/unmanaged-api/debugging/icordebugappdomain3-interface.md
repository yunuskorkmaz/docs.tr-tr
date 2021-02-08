---
description: 'Daha fazla bilgi edinin: ICorDebugAppDomain3 Interface'
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
ms.openlocfilehash: 6575aa685759102443babeaf82774e6221b80693
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772217"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 Arabirimi

Bir uygulama etki alanında yüklü olan Windows Çalışma Zamanı türlerinin yönetilen temsilleri hakkında bilgi almak için yöntemler sağlar. Bu arabirim, ICorDebugAppDomain ve ICorDebugAppDomain2 arabirimlerinin bir uzantısıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ICorDebugAppDomain3:: Getcachedwınrttypes](icordebugappdomain3-getcachedwinrttypes-method.md)|Tüm önbelleğe alınmış Windows Çalışma Zamanı türleri için bir Numaralandırıcı alır.|  
|[ICorDebugAppDomain3:: Getcachedwinrttypesforiıds](icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Bir uygulama etki alanındaki önbelleğe alınmış Windows Çalışma Zamanı türleri için kendi arabirim tanımlayıcılarına göre bir Numaralandırıcı alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu arabirim bir hata ayıklayıcı tarafından, bir işlev değerlendirme çağrısıyla birlikte kullanılmak üzere tasarlanmıştır `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)` . Yöntemi bir Windows Çalışma Zamanı sunucusu nesnesi tarafından desteklenen arabirim tanımlayıcılarını aldığında, hata ayıklayıcı bu arayüzlere karşılık gelen yönetilen türlerle eşlemek için bu arabirimde tanımlanan yöntemleri kullanabilir.  
  
 Bu arabirimin bir örneğini almak için `QueryInterface` ICorDebugAppDomain veya ICorDebugAppDomain2 arabiriminin bir örneği üzerinde çalıştırın.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Windows Çalışma Zamanı  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)

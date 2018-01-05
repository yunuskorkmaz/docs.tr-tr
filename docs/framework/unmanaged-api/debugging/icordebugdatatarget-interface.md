---
title: ICorDebugDataTarget Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5d3a3b190cfa606bd4239e24c5defdaff9f4257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget Arabirimi
Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPlatform Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|İşlemci mimarisi ve hedef işlemin çalıştığı işletim sistemi dahil olmak üzere bu platform hakkında bilgi sağlar.|  
|[ReadVirtual Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Belirtilen adresten başlayarak bitişik bellek bloğu alır ve sağlanan arabellek döndürür.|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Belirtilen iş parçacığı için geçerli iş parçacığının içeriği ister.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugDataTarget`ve yöntemlerinden aşağıdaki özelliklere sahiptir:  
  
-   Hata Ayıklama Hizmetleri, bellek ve diğer verileri hedef işleminde erişmek için bu arabirimde yöntemlerini çağırın.  
  
-   Hata ayıklayıcı istemci belirli bir hedef (örneğin, canlı bir işlem ya da bir bellek dökümü) için uygun şekilde bu arabirimi uygulamalıdır.  
  
-   `ICorDebugDataTarget` Yöntemleri çağrılabilir yalnızca diğer uygulanan yöntemleri içinde `ICorDebug*` arabirimleri. Bu hata ayıklayıcı istemci sahip denetim hangi iş parçacığı üzerinde ve ne zaman çağrılır sağlar.  
  
-   `ICorDebugDataTarget` Uygulama hedef hakkında güncel bilgileri her zaman döndürmesi gerekir.  
  
 Hedef işlem durduruldu ve gerekir sırasında herhangi bir şekilde değiştirilmez `ICorDebug*` arabirimleri (ve bu nedenle `ICorDebugDataTarget` yöntemleri) adı verilir. Hedef, durum değişikliklerini ve canlı bir işlem ise [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi sahip yeniden değiştirme Icordebugprocess örneği sağlamak için çağrılabilir.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

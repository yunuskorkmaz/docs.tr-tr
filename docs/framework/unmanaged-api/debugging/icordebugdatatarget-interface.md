---
title: ICorDebugDataTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: 9029d53872108bc1953fd22c584b6e01a6f3c7ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788865"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget Arabirimi
Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetPlatform Yöntemi](icordebugdatatarget-getplatform-method.md)|Hedef işlemin çalıştığı işlemci mimarisi ve işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.|  
|[ReadVirtual Yöntemi](icordebugdatatarget-readvirtual-method.md)|Belirtilen adresten başlayarak bir ardışık bellek bloğunu alır ve sağlanan arabellekte döndürür.|  
|[GetThreadContext Yöntemi](icordebugdatatarget-getthreadcontext-method.md)|Belirtilen iş parçacığı için geçerli iş parçacığı bağlamını ister.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugDataTarget` ve yöntemleri aşağıdaki özelliklere sahiptir:  
  
- Hata ayıklama Hizmetleri, hedef işlemdeki belleğe ve diğer verilere erişmek için bu arabirimdeki yöntemleri çağırır.  
  
- Hata ayıklayıcı istemcisinin, bu arabirimi belirli bir hedefe (örneğin, canlı bir işlem veya bir bellek dökümü) uygun şekilde uygulaması gerekir.  
  
- `ICorDebugDataTarget` yöntemleri yalnızca diğer `ICorDebug*` arabirimlerinde uygulanan yöntemlerin içinden çağrılabilir. Bu, hata ayıklayıcı istemcisinin üzerinde çağrıldığı iş parçacığı üzerinde denetim sahibi olmasını sağlar.  
  
- `ICorDebugDataTarget` uygulama, hedefle ilgili her zaman güncel bilgiler döndürmelidir.  
  
 Hedef işlem durdurulmalı ve `ICorDebug*` arabirimleri (ve bu nedenle `ICorDebugDataTarget` yöntemleri) çağrıldığında hiçbir şekilde değiştirilmemelidir. Hedef canlı bir işlemdir ve durumu değişirse, bir değiştirme ICorDebugProcess örneği sağlamak için [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yönteminin yeniden çağrılması gerekir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)

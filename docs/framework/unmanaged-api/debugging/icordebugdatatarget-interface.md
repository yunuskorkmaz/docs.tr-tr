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
ms.openlocfilehash: 54272dd18a12715bab58ec1b1a4c1dc00e4bf12b
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976531"
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
 `ICorDebugDataTarget`ve yöntemleri aşağıdaki özelliklere sahiptir:  
  
- Hata ayıklama Hizmetleri, hedef işlemdeki belleğe ve diğer verilere erişmek için bu arabirimdeki yöntemleri çağırır.  
  
- Hata ayıklayıcı istemcisinin, bu arabirimi belirli bir hedefe (örneğin, canlı bir işlem veya bir bellek dökümü) uygun şekilde uygulaması gerekir.  
  
- `ICorDebugDataTarget` Yöntemler yalnızca diğer `ICorDebug*` arabirimlerde uygulanan metotların içinden çağrılabilir. Bu, hata ayıklayıcı istemcisinin üzerinde çağrıldığı iş parçacığı üzerinde denetim sahibi olmasını sağlar.  
  
- `ICorDebugDataTarget` Uygulamanın, hedefle ilgili her zaman güncel bilgileri döndürmesi gerekir.  
  
 Hedef işlem durdurulmalı ve `ICorDebug*` arabirimler (ve bu nedenle `ICorDebugDataTarget` Yöntemler) çağrıldığında hiçbir şekilde değiştirilmemelidir. Hedef canlı bir işlemdir ve durumu değişirse, bir değiştirme ICorDebugProcess örneği sağlamak için [ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yönteminin yeniden çağrılması gerekir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)

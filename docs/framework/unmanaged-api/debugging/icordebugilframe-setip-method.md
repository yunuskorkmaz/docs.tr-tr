---
title: ICorDebugILFrame::SetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 466fe421f4ff3f8983159ccb38503b75551c87bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788551"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP Yöntemi
Yönerge işaretçisini, Microsoft ara dili (MSIL) kodunda belirtilen konum konumunu ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nOffset`  
 MSIL kodunda konum konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetIP` çağrıları, geçerli iş parçacığı için tüm çerçeveleri ve zincirleri hemen geçersiz kılar. Hata ayıklayıcı `SetIP`çağrısından sonra çerçeve bilgilerine ihtiyaç duyuyorsa, yeni bir yığın izlemesi gerçekleştirmelidir.  
  
 [ICorDebug](icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak. Ancak, çerçeve geçerli bir durumdaysa bile başlatılmamış yerel değişkenler gibi sorunlar olabilir. Çağıran, çalışan programın tutarlılığına ilişkin emin olmanın sorumluluğundadır.  
  
 64 bit platformlarda, yönerge işaretçisi bir `catch` veya `finally` bloğunun dışına taşınamaz. `SetIP`, 64 bitlik bir platformda böyle bir geçiş yapmak için çağrılırsa, hata belirten bir HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

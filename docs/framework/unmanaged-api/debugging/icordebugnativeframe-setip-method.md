---
title: ICorDebugNativeFrame::SetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: bc33768e4155a0e272d3374d4c586c79ef2ff3fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792774"
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP Yöntemi
Yönerge işaretçisini yerel kodda belirtilen konum konumunu ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nOffset`  
 'ndaki Yerel koddaki konum konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetIP` çağrıları, geçerli iş parçacığı için tüm çerçeveleri ve zincirleri hemen geçersiz kılar. Hata ayıklayıcı `SetIP`çağrısından sonra çerçeve bilgilerine ihtiyaç duyuyorsa, yeni bir yığın izlemesi gerçekleştirmelidir.  
  
 [ICorDebug](icordebug-interface.md) , yığın çerçevesini geçerli bir durumda tutmaya çalışacak. Ancak, çerçeve geçerli bir durumda olsa da, çalışma zamanı ele aldığına bağlı olarak, başlatılmamış yerel değişkenler gibi sorunlar da olabilir ve bu şekilde devam eder. Çağıran, çalışan programın ayırt edilemeyen bir şekilde sorumludur.  
  
 64 bit platformlarda, yönerge işaretçisi bir `catch` veya `finally` bloğunun dışına taşınamaz. `SetIP`, 64 bitlik bir platformda böyle bir geçiş yapmak için çağrılırsa, hata belirten bir HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

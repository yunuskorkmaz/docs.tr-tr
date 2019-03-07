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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33a4315d8908906e9ae1511aa9501969752d4af6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484871"
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP Yöntemi
Yönerge işaretçisi yerel kodda uzaklık belirtilen konuma ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nOffset`  
 [in] Yerel kodda uzaklık konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrılar `SetIP` hemen tüm çerçeveleri ve zincirleri için geçerli iş parçacığı geçersiz. Hata ayıklayıcı çağrısı yapıldıktan sonra çerçeve bilgileri gerekiyorsa `SetIP`, yeni bir yığın izlemesi gerçekleştirmeniz gerekir.  
  
 [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yığın çerçevesini geçerli bir durumda tutmak çalışacaktır. Ancak, çalışma zamanı ilgili olduğu kadar çerçeveyi geçerli bir durumda olsa bile, yine de olabilir başlatılmamış yerel değişkenler vb. gibi sorunlar. Çalışan programa önbelleklerinin sağlamak için çağıran sorumludur.  
  
 64-bit platformlarda, yönerge işaretçisini tanesi taşınamaz bir `catch` veya `finally` blok. Varsa `SetIP` çağrılır böyle bir 64-bit platformlarda hareket ettirmek için hata olduğunu gösteren bir HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.


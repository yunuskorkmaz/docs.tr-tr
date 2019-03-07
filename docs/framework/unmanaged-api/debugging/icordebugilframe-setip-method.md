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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a25e52c6b858aaa602ffade0e407b1aaf6e5c67e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471400"
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP Yöntemi
Microsoft Ara dil (MSIL) kodu belirtilen uzaklık konuma yönerge işaretçisini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `nOffset`  
 MSIL kodu uzaklık konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrılar `SetIP` hemen tüm çerçeveleri ve zincirleri için geçerli iş parçacığı geçersiz. Hata ayıklayıcı çağrısı yapıldıktan sonra çerçeve bilgileri gerekiyorsa `SetIP`, yeni bir yığın izlemesi gerçekleştirmeniz gerekir.  
  
 [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yığın çerçevesini geçerli bir durumda tutmak çalışacaktır. Ancak, çerçeve geçerli bir durumda olsa bile, yine de olabilir başlatılmamış yerel değişkenler gibi sorunlar. Çağıran, çalışan programa önbelleklerinin sağlamaktan sorumludur.  
  
 64-bit platformlarda, yönerge işaretçisini tanesi taşınamaz bir `catch` veya `finally` blok. Varsa `SetIP` çağrılır böyle bir 64-bit platformlarda hareket ettirmek için hata olduğunu gösteren bir HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

---
title: "ICorDebugNativeFrame::SetIP Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25b4f42eb6f10ecade468824d9d790a2bce740a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframesetip-method"></a>ICorDebugNativeFrame::SetIP Yöntemi
Yönerge işaretçisi yerel kodda belirtilen uzaklık konumunu ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `nOffset`  
 [in] Yerel kodda uzaklık konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrılar `SetIP` hemen tüm çerçeveler ve zincirleri geçerli iş parçacığı için geçersiz. Hata ayıklayıcı çerçeve bilgileri yapılan bir çağrı sonra gerekirse `SetIP`, yeni bir yığın izlemesi gerçekleştirmelisiniz.  
  
 [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yığın çerçevesi geçerli bir durumda tutmak deneyecek. Ancak, çalışma zamanı ilgili olduğu kadar çerçeve geçerli bir durumda olsa bile, yine olabilir başlatılmayan yerel değişkenlerde vb. gibi sorunlar. Çağıran, çalışan program önbelleklerinin sağlamak için sorumludur.  
  
 64 bit platformlarda dışı yönerge işaretçisi taşınamaz bir `catch` veya `finally` bloğu. Varsa `SetIP` çağrılır böyle bir 64-bit platformu üzerinde hareket ettirmek için hata olduğunu gösteren bir HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 

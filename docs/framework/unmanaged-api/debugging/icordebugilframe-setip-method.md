---
title: "ICorDebugILFrame::SetIP Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daffbbd9e961f4fdc7ff2e3c9be57e41e8fa3f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP Yöntemi
Yönerge işaretçisi Microsoft Ara dili (MSIL) kodda belirtilen uzaklık konumuna ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `nOffset`  
 MSIL kodda uzaklık konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrılar `SetIP` hemen tüm çerçeveler ve zincirleri geçerli iş parçacığı için geçersiz. Hata ayıklayıcı çerçeve bilgileri yapılan bir çağrı sonra gerekirse `SetIP`, yeni bir yığın izlemesi gerçekleştirmelisiniz.  
  
 [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) yığın çerçevesi geçerli bir durumda tutmak deneyecek. Ancak, çerçeve geçerli bir durumda olsa bile, yine sorunları olabilir başlatılmayan yerel değişkenlerde gibi. Çağıran, çalışan program önbelleklerinin sağlamak için sorumludur.  
  
 64 bit platformlarda dışı yönerge işaretçisi taşınamaz bir `catch` veya `finally` bloğu. Varsa `SetIP` çağrılır böyle bir 64-bit platformu üzerinde hareket ettirmek için hata olduğunu gösteren bir HRESULT döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

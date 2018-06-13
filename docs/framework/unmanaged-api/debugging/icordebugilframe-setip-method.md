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
ms.openlocfilehash: ed7de70c8ea26f46f44abb3e063c6e4c4b115666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414496"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

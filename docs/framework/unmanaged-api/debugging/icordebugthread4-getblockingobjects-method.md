---
title: ICorDebugThread4::GetBlockingObjects Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetBlockingObjects Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 006535885868ef2778146f86e5395ea1f7605d6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects Metodu
Sıralanmış numaralandırması sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) sağlamak yapıları iş parçacığı engelleme bilgi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppBlockingObjectEnum`  
 [out] Sıralanmış numaralandırması için bir işaretçi [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen listedeki ilk öğe iş parçacığı engelleme ilk yapısına karşılık gelir. İkinci öğe ilk ve benzeri engellenen zaman uyumsuz yordam çağrısı (APC) çalışırken karşılaşılan bir engelleme öğesi karşılık gelir.  
  
 Numaralandırma yalnızca geçerli eşitlenmiş durumuna süre için geçerli değil.  
  
 Ayıklayıcı eşitlenmiş durumda olsa da bu yöntemi çağrılmalıdır.  
  
 Varsa `ppBlockingObjectEnum` geçerli bir işaretçi değil sonucu tanımlanmadı.  
  
 Bir iş parçacığı engellenir ve hata belirlenemiyor olursa yöntemi hata olduğunu gösteren bir HRESULT verir; Aksi takdirde, S_OK döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugThread4 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

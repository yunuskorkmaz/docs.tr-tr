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
ms.openlocfilehash: 6783d7f9af67acdff147cc46ea4f856f9b10bf3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Icordebugthread4 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)

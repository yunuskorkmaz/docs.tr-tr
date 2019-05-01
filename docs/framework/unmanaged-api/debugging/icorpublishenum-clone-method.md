---
title: ICorPublishEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0ce1d8c0074f62d35e16465b368269e233a713b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993531"
---
# <a name="icorpublishenumclone-method"></a>ICorPublishEnum::Clone Yöntemi
Bu bir kopyasını oluşturur [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEnum`  
 [out] Adresine bir işaretçi bir `ICorPublishEnum` bu kopyasını nesnesini `ICorPublishEnum` nesnesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)

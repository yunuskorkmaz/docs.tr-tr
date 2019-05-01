---
title: ICorPublishProcessEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 169716d1a6d0dd633821cc832de96c9a02958d76
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986597"
---
# <a name="icorpublishprocessenumnext-method"></a>ICorPublishProcessEnum::Next Yöntemi
Geçerli imleç konumundan başlayarak koleksiyon belirtilen işlem sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Alınacak işlemlerin sayısı.  
  
 `objects`  
 [out] Bir işaretçi dizisinin işaretçisi alınan [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) her biri bir işlemi temsil eden nesneleri.  
  
 `pceltFetched`  
 [out] Gerçekte döndürülen işlem sayısı için işaretçi. Bu değer null olabilir, `celt` biridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishProcessEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)

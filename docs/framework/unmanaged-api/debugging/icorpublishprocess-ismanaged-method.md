---
title: ICorPublishProcess::IsManaged Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29c5f96bab374d6e2d43424370bff2a4a2ab6df3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986599"
---
# <a name="icorpublishprocessismanaged-method"></a>ICorPublishProcess::IsManaged Yöntemi
İşlem bu tarafından başvurulan olup olmadığını gösteren bir değer alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) yönetilen kod adı verilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbManaged`  
 [out] İşlem yönetilen kod olup olmadığını gösteren bir Boole değeri için bir işaretçi. Değer `true` işlem kodu; yönetiliyorsa Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Geçerli sürümü bu yana `ICorPublishProcess` erişimine yalnızca yönetilen kod, işlemleri izin veren `IsManaged` her zaman döndürür `true`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishProcess Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)

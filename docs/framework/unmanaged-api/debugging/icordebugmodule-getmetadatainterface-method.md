---
title: ICorDebugModule::GetMetaDataInterface Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d374b83155ccc8511c6e3217a8a49819d81a7d48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface Metodu
Modül için meta verileri incelemek için kullanılan bir meta veri arabirimi nesnesi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `riid`  
 [in] Meta veri arabirimi belirtir başvuru kimliği.  
  
 `ppObj`  
 [out] Adresine bir işaretçi bir `T:IUnknown` biri nesne [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklayıcı kullanabilirsiniz `GetMetaDataInterface` yöntemi orijinal meta verileri bu modül düzenlemek için yapmanız gerekir bir modül için bir kopyasını oluşturun. Hata ayıklayıcı çağrıları `GetMetaDataInterface` almak için bir [Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) arabirimi nesnesi için modülü, daha sonra çağırır [Imetadataemit::savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) bellek modülün meta verilerinin bir kopyasını kaydetmek için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veriler](../../../../docs/framework/unmanaged-api/metadata/index.md)

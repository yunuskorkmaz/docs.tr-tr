---
title: "ICorDebugILFrame2::EnumerateTypeParameters Yöntemi"
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
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9180ea68dde667ffe0dc8e15b98cb82efaa667ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters Yöntemi
İçeren bir Icordebugtypeenum nesne alır <xref:System.Type> bu çerçevesinde parametreleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppTyParEnum`  
 Tür parametreleri listesi veren bir Icordebugtypeenum arabirimi nesnesi adresini gösteren bir işaretçi.  
  
 Tür parametreleri listesini (varsa) ve ardından yöntemi türü parametrelerini sınıfı tür parametreleri (varsa) içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [Imetadataımport2::enumgenericparams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) kaç sınıfı tür parametreleri ve yöntemi türü bu listeyi içeren parametreleri belirlemek amacıyla yöntemi.  
  
 Tür parametreleri her zaman kullanılabilir değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

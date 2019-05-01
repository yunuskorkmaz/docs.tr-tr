---
title: ICorDebugILFrame2::EnumerateTypeParameters Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7454b551edc546fecbd9d091f7c821e0a07b16df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988553"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a>ICorDebugILFrame2::EnumerateTypeParameters Yöntemi
Icordebugtypeenum nesneyi içeren alır <xref:System.Type> bu çerçeve parametreleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppTyParEnum`  
 Numaralandırma tür parametrelerinin izin veren bir Icordebugtypeenum arabirimi nesnesi adresi için bir işaretçi.  
  
 Tür parametreleri listesi tarafından yöntemi tür parametreleri (varsa) ve ardından sınıf türündeki parametrelere (varsa) içerir.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanım [Imetadataımport2::enumgenericparams](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md) kaç sınıf türündeki parametrelere ve yöntem parametreleri içeren bu liste türünü belirlemek için yöntemi.  
  
 Tür parametreleri her zaman kullanılabilir değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

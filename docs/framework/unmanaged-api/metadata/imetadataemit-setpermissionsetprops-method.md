---
title: IMetaDataEmit::SetPermissionSetProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8a4d3b7014d0da88e83b507c39c039d39ba93d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542684"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a>IMetaDataEmit::SetPermissionSetProps Yöntemi
Ayarlar veya önceki bir çağrı tarafından tanımlanan bir izin kümesi meta veri imzası özelliklerini güncelleştirir [Imetadataemit::definepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `tk`  
 [in] Nesne ile kullanılabilir temsil eden bir meta veri belirteci.  
  
 `dwAction`  
 [in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) kullanılacak bildirim temelli güvenlik türünü belirten bir değer.  
  
 `pvPermission`  
 [in] BLOB izni.  
  
 `cbPermission`  
 [in] Bayt cinsinden boyutu, `pvPermission`.  
  
 `ppm`  
 [out] Bir `mdPermission` güncelleştirilmiş izinleri temsil eden bir meta veri belirteci.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

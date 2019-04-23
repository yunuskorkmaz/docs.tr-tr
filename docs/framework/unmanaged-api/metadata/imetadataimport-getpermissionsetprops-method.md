---
title: IMetaDataImport::GetPermissionSetProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ff91a24dec7f8507989b701ea24b569c1670c89
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109721"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a>IMetaDataImport::GetPermissionSetProps Yöntemi
İle ilişkili meta verileri alır <xref:System.Security.PermissionSet?displayProperty=nameWithType> belirtilen izni belirteci tarafından temsil edilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pm`  
 [in] İzin için meta veri özelliklerini almak için kümesini temsil eden izin meta veri belirteci.  
  
 `pdwAction`  
 [out] İzin kümesi için bir işaretçi.  
  
 `ppvPermission`  
 [out] İzin kümesi ikili meta veri imzası bir işaretçi.  
  
 `pcbPermission`  
 [out] Bayt cinsinden boyutu `ppvPermission`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.PermissionSet>
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

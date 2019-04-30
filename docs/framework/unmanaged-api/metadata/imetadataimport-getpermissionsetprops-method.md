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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777621"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="6d15e-102">IMetaDataImport::GetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d15e-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="6d15e-103">İle ilişkili meta verileri alır <xref:System.Security.PermissionSet?displayProperty=nameWithType> belirtilen izni belirteci tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="6d15e-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d15e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d15e-104">Syntax</span></span>  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d15e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d15e-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="6d15e-106">[in] İzin için meta veri özelliklerini almak için kümesini temsil eden izin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="6d15e-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="6d15e-107">[out] İzin kümesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d15e-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="6d15e-108">[out] İzin kümesi ikili meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d15e-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="6d15e-109">[out] Bayt cinsinden boyutu `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="6d15e-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d15e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d15e-110">Requirements</span></span>  
 <span data-ttu-id="6d15e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d15e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d15e-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6d15e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d15e-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6d15e-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d15e-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d15e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d15e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d15e-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="6d15e-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d15e-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6d15e-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6d15e-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

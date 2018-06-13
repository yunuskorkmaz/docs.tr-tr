---
title: IMetaDataImport::GetPermissionSetProps Metodu
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
ms.openlocfilehash: be9b2fa3037dc00bce52d9ff89291d1c02cffc38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449305"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="e5236-102">IMetaDataImport::GetPermissionSetProps Metodu</span><span class="sxs-lookup"><span data-stu-id="e5236-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="e5236-103">İle ilişkili meta verileri alır <xref:System.Security.PermissionSet?displayProperty=nameWithType> belirtilen izni belirteç tarafından temsil edilen.</span><span class="sxs-lookup"><span data-stu-id="e5236-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5236-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5236-104">Syntax</span></span>  
  
```  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5236-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5236-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="e5236-106">[in] Meta veri özelliklerini almak için izni temsil eden izni meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="e5236-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="e5236-107">[out] İzin kümesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5236-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="e5236-108">[out] İkili meta veri imzası izin kümesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5236-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="e5236-109">[out] Bayt cinsinden boyutu `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="e5236-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5236-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5236-110">Requirements</span></span>  
 <span data-ttu-id="e5236-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5236-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5236-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5236-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5236-113">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e5236-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5236-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5236-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5236-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5236-115">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 [<span data-ttu-id="e5236-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5236-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e5236-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5236-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

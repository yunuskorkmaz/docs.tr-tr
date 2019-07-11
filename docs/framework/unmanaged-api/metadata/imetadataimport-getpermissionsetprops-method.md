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
ms.openlocfilehash: 48cd62f89f1112a1007a5661dc55fe2977dace2b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778909"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="4242b-102">IMetaDataImport::GetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4242b-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="4242b-103">İle ilişkili meta verileri alır <xref:System.Security.PermissionSet?displayProperty=nameWithType> belirtilen izni belirteci tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="4242b-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4242b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4242b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4242b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4242b-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="4242b-106">[in] İzin için meta veri özelliklerini almak için kümesini temsil eden izin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4242b-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="4242b-107">[out] İzin kümesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4242b-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="4242b-108">[out] İzin kümesi ikili meta veri imzası bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4242b-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="4242b-109">[out] Bayt cinsinden boyutu `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="4242b-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4242b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4242b-110">Requirements</span></span>  
 <span data-ttu-id="4242b-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4242b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4242b-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="4242b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4242b-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4242b-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4242b-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4242b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4242b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4242b-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="4242b-116">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4242b-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4242b-117">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4242b-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)

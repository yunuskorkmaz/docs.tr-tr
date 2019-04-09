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
ms.openlocfilehash: 510c33b8e0e26bead00dcb85a6ceba102a5f267d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163780"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="2d118-102">IMetaDataEmit::SetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d118-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="2d118-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir izin kümesi meta veri imzası özelliklerini güncelleştirir [Imetadataemit::definepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="2d118-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d118-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d118-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d118-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d118-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="2d118-106">[in] Nesne ile kullanılabilir temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="2d118-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="2d118-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) kullanılacak bildirim temelli güvenlik türünü belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="2d118-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="2d118-108">[in] BLOB izni.</span><span class="sxs-lookup"><span data-stu-id="2d118-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="2d118-109">[in] Bayt cinsinden boyutu, `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="2d118-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="2d118-110">[out] Bir `mdPermission` güncelleştirilmiş izinleri temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="2d118-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d118-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d118-111">Requirements</span></span>  
 <span data-ttu-id="2d118-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d118-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d118-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2d118-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d118-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="2d118-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2d118-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2d118-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2d118-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d118-116">See also</span></span>

- [<span data-ttu-id="2d118-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d118-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2d118-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d118-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

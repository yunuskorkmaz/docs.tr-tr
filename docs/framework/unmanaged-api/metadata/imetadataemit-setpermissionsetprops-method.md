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
ms.openlocfilehash: 8d80e3206f74c3c50c8436563b0e39d1229a963b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446375"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="83088-102">IMetaDataEmit::SetPermissionSetProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83088-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="83088-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir izin kümesi meta verileri imzası özelliklerini güncelleştirir [Imetadataemit::definepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="83088-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83088-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83088-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83088-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83088-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="83088-106">[in] Donatılmış için nesnesini temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="83088-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="83088-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) kullanılacak bildirim temelli güvenlik türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="83088-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="83088-108">[in] BLOB izni.</span><span class="sxs-lookup"><span data-stu-id="83088-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="83088-109">[in] Bayt olarak boyutu, `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="83088-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="83088-110">[out] Bir `mdPermission` güncelleştirilmiş izinleri gösteren meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="83088-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83088-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83088-111">Requirements</span></span>  
 <span data-ttu-id="83088-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83088-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83088-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="83088-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83088-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="83088-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83088-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83088-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83088-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83088-116">See Also</span></span>  
 [<span data-ttu-id="83088-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83088-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="83088-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83088-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

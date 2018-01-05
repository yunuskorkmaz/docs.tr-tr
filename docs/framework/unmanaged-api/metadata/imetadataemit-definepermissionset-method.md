---
title: "IMetaDataEmit::DefinePermissionSet Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefinePermissionSet
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 74bea316d3f56e007c4b75e6b801d8c82ae8ce96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="3157b-102">IMetaDataEmit::DefinePermissionSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3157b-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="3157b-103">Bir izin kümesi ile belirtilen metadata imza için bir tanım oluşturur ve bu izin kümesi tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="3157b-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3157b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3157b-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3157b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3157b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="3157b-106">[in] Donatılmış nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3157b-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="3157b-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) kullanılacak bildirim temelli güvenlik türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="3157b-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="3157b-108">[in] BLOB izni.</span><span class="sxs-lookup"><span data-stu-id="3157b-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="3157b-109">[in] Bayt olarak boyutu, `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="3157b-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="3157b-110">[out] Döndürülen izni belirteci.</span><span class="sxs-lookup"><span data-stu-id="3157b-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3157b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3157b-111">Requirements</span></span>  
 <span data-ttu-id="3157b-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3157b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3157b-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3157b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3157b-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3157b-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3157b-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3157b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3157b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3157b-116">See Also</span></span>  
 [<span data-ttu-id="3157b-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3157b-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="3157b-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3157b-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

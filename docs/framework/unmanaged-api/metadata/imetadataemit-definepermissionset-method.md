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
ms.openlocfilehash: 6a503f22710f392ecbb0ae2704d2c2950a858c30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="a9fe8-102">IMetaDataEmit::DefinePermissionSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9fe8-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="a9fe8-103">Bir izin kümesi ile belirtilen metadata imza için bir tanım oluşturur ve bu izin kümesi tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="a9fe8-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9fe8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9fe8-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9fe8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9fe8-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a9fe8-106">[in] Donatılmış nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a9fe8-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="a9fe8-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) kullanılacak bildirim temelli güvenlik türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="a9fe8-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="a9fe8-108">[in] BLOB izni.</span><span class="sxs-lookup"><span data-stu-id="a9fe8-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="a9fe8-109">[in] Bayt olarak boyutu, `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="a9fe8-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="a9fe8-110">[out] Döndürülen izni belirteci.</span><span class="sxs-lookup"><span data-stu-id="a9fe8-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9fe8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9fe8-111">Requirements</span></span>  
 <span data-ttu-id="a9fe8-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9fe8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9fe8-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a9fe8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9fe8-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a9fe8-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9fe8-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9fe8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9fe8-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9fe8-116">See Also</span></span>  
 [<span data-ttu-id="a9fe8-117">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9fe8-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a9fe8-118">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9fe8-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

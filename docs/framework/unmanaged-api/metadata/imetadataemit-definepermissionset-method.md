---
title: IMetaDataEmit::DefinePermissionSet Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05339787b112ad029cb9870e8c6ffca37e55e631
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445195"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="5a871-102">IMetaDataEmit::DefinePermissionSet Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a871-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="5a871-103">Bir izin kümesi ile belirtilen metadata imza için bir tanım oluşturur ve bu izin kümesi tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="5a871-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a871-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a871-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a871-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a871-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5a871-106">[in] Donatılmış nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5a871-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="5a871-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) kullanılacak bildirim temelli güvenlik türünü belirten değer.</span><span class="sxs-lookup"><span data-stu-id="5a871-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="5a871-108">[in] BLOB izni.</span><span class="sxs-lookup"><span data-stu-id="5a871-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="5a871-109">[in] Bayt olarak boyutu, `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="5a871-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="5a871-110">[out] Döndürülen izni belirteci.</span><span class="sxs-lookup"><span data-stu-id="5a871-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a871-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a871-111">Requirements</span></span>  
 <span data-ttu-id="5a871-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a871-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a871-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5a871-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a871-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5a871-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a871-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a871-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a871-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a871-116">See Also</span></span>  
 [<span data-ttu-id="5a871-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a871-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5a871-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a871-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

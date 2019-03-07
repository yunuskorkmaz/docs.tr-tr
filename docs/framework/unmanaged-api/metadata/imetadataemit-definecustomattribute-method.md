---
title: IMetaDataEmit::DefineCustomAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adf3c74526bbf2b8e740f505ab6f4243cd799041
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474585"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="48b1c-102">IMetaDataEmit::DefineCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48b1c-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="48b1c-103">Belirtilen nesneyi, eklenecek belirtilen meta veri imzası ile özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="48b1c-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b1c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48b1c-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48b1c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48b1c-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="48b1c-106">[in] Sahip öğe için belirteç.</span><span class="sxs-lookup"><span data-stu-id="48b1c-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="48b1c-107">[in] Özel öznitelik tanımlayan belirteç.</span><span class="sxs-lookup"><span data-stu-id="48b1c-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="48b1c-108">[in] Özel öznitelik için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="48b1c-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="48b1c-109">[in] Bayt sayısı `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="48b1c-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="48b1c-110">[out] `mdCustomAttribute` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="48b1c-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b1c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48b1c-111">Requirements</span></span>  
 <span data-ttu-id="48b1c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48b1c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48b1c-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="48b1c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="48b1c-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="48b1c-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48b1c-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48b1c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b1c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48b1c-116">See also</span></span>
- [<span data-ttu-id="48b1c-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48b1c-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="48b1c-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48b1c-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

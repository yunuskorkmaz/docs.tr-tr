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
ms.openlocfilehash: 52190583338f1c1ee9183a98d5f4a6cd7236342d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075692"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="72837-102">IMetaDataEmit::DefineCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72837-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="72837-103">Belirtilen nesneyi, eklenecek belirtilen meta veri imzası ile özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="72837-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72837-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72837-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72837-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72837-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="72837-106">[in] Sahip öğe için belirteç.</span><span class="sxs-lookup"><span data-stu-id="72837-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="72837-107">[in] Özel öznitelik tanımlayan belirteç.</span><span class="sxs-lookup"><span data-stu-id="72837-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="72837-108">[in] Özel öznitelik için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72837-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="72837-109">[in] Bayt sayısı `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="72837-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="72837-110">[out] `mdCustomAttribute` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="72837-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72837-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72837-111">Requirements</span></span>  
 <span data-ttu-id="72837-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72837-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72837-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="72837-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72837-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="72837-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72837-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72837-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72837-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72837-116">See also</span></span>

- [<span data-ttu-id="72837-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72837-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="72837-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72837-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

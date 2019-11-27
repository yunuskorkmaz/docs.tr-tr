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
ms.openlocfilehash: e6a732b98ae02ba2b273b45921b7de61ab4fd29f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432645"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="17580-102">IMetaDataEmit::DefineCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17580-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="17580-103">Belirtilen nesneye iliştirililmesi için belirtilen meta veri imzasına sahip özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="17580-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17580-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17580-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17580-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17580-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="17580-106">'ndaki Sahip öğesi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="17580-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="17580-107">'ndaki Özel özniteliği tanımlayan belirteç.</span><span class="sxs-lookup"><span data-stu-id="17580-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="17580-108">'ndaki Özel özniteliğe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="17580-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="17580-109">'ndaki `pCustomAttribute`bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="17580-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="17580-110">dışı `mdCustomAttribute` belirteci atandı.</span><span class="sxs-lookup"><span data-stu-id="17580-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17580-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17580-111">Requirements</span></span>  
 <span data-ttu-id="17580-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17580-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17580-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="17580-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17580-114">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="17580-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17580-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17580-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17580-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17580-116">See also</span></span>

- [<span data-ttu-id="17580-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17580-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="17580-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17580-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

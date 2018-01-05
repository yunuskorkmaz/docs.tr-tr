---
title: "IMetaDataEmit::DefineNestedType Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineNestedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99250d98f9ffd90857128aa5d8a675a997926bf5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="7188c-102">IMetaDataEmit::DefineNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7188c-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="7188c-103">Tür tanımı meta verileri imza oluşturur, döndürür bir `mdTypeDef` belirteci bu tür için ve tanımlanmış türü tarafından başvurulan türünün bir üyesi olduğunu belirtir `tdEncloser` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7188c-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7188c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7188c-104">Syntax</span></span>  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7188c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7188c-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="7188c-106">[in] Unicode türünün adı.</span><span class="sxs-lookup"><span data-stu-id="7188c-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="7188c-107">[in] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="7188c-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="7188c-108">Bu, bir bit maskesi olan `CorTypeAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="7188c-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="7188c-109">[in] Belirtecin temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="7188c-109">[in] The token of the base class.</span></span> <span data-ttu-id="7188c-110">Bu olan bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="7188c-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="7188c-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="7188c-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="7188c-112">[in] Bu sınıf veya arabirimi uygulayan arabirimler belirtin belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="7188c-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="7188c-113">[in] Kendilerini kapsayan türle belirteç.</span><span class="sxs-lookup"><span data-stu-id="7188c-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="7188c-114">Dizinin son öğesi olmalı `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="7188c-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="7188c-115">[out] `mdTypeDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="7188c-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7188c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7188c-116">Requirements</span></span>  
 <span data-ttu-id="7188c-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7188c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7188c-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7188c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7188c-119">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7188c-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7188c-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7188c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7188c-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7188c-121">See Also</span></span>  
 [<span data-ttu-id="7188c-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7188c-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7188c-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7188c-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

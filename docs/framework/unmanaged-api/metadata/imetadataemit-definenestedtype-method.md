---
title: IMetaDataEmit::DefineNestedType Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ebd4e9beca315ef8284c915800afec6bdb78c78
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62044011"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="1568b-102">IMetaDataEmit::DefineNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1568b-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="1568b-103">Meta veri imzası bir tür tanımı oluşturur, döndürür bir `mdTypeDef` bu tür için belirteç ve tanımlanan bir tür tarafından başvurulan tür üyesi olduğunu belirtir `tdEncloser` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1568b-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1568b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1568b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1568b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1568b-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="1568b-106">[in] Unicode türünün adı.</span><span class="sxs-lookup"><span data-stu-id="1568b-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="1568b-107">[in] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="1568b-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="1568b-108">Bu, bir bit maskesi, `CorTypeAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="1568b-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="1568b-109">[in] Belirteç temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="1568b-109">[in] The token of the base class.</span></span> <span data-ttu-id="1568b-110">Bu bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="1568b-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="1568b-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="1568b-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="1568b-112">[in] Bu sınıf veya arabirim uyguladığı arabirimlerin belirtin belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="1568b-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="1568b-113">[in] Kapsayan türdeki belirteç.</span><span class="sxs-lookup"><span data-stu-id="1568b-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="1568b-114">Dizinin son öğesi olmalı `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="1568b-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="1568b-115">[out] `mdTypeDef` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="1568b-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1568b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1568b-116">Requirements</span></span>  
 <span data-ttu-id="1568b-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1568b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1568b-118">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1568b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1568b-119">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1568b-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1568b-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1568b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1568b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1568b-121">See also</span></span>

- [<span data-ttu-id="1568b-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1568b-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1568b-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1568b-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

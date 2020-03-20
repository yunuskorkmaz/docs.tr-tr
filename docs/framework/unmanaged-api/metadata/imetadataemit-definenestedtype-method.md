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
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175817"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="0efcf-102">IMetaDataEmit::DefineNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0efcf-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="0efcf-103">Bir tür tanımının meta veri imzasını `mdTypeDef` oluşturur, bu tür için bir belirteç döndürür ve tanımlanan `tdEncloser` türün parametre tarafından başvurulan türe üye olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0efcf-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efcf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0efcf-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0efcf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0efcf-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="0efcf-106">[içinde] Unicode'daki türün adı.</span><span class="sxs-lookup"><span data-stu-id="0efcf-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="0efcf-107">[içinde] `TypeDef` öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="0efcf-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="0efcf-108">Bu `CorTypeAttr` değerlerin bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="0efcf-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="0efcf-109">[içinde] Taban sınıfın belirteci.</span><span class="sxs-lookup"><span data-stu-id="0efcf-109">[in] The token of the base class.</span></span> <span data-ttu-id="0efcf-110">Bu ya `mdTypeDef` bir `mdTypeRef` ya da bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="0efcf-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="0efcf-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="0efcf-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="0efcf-112">[içinde] Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten belirteçler dizisi.</span><span class="sxs-lookup"><span data-stu-id="0efcf-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="0efcf-113">[içinde] Çevreleyen türün belirteci.</span><span class="sxs-lookup"><span data-stu-id="0efcf-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="0efcf-114">Dizinin son öğesi `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="0efcf-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="0efcf-115">[çıkış] Atanan `mdTypeDef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="0efcf-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0efcf-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0efcf-116">Requirements</span></span>  
 <span data-ttu-id="0efcf-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0efcf-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0efcf-118">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0efcf-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0efcf-119">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0efcf-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0efcf-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0efcf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0efcf-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0efcf-121">See also</span></span>

- [<span data-ttu-id="0efcf-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0efcf-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0efcf-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0efcf-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

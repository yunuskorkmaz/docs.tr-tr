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
ms.openlocfilehash: 2b24c2ca6907dfdb63ad934ec30557c246db174c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004362"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="41483-102">IMetaDataEmit::DefineNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41483-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="41483-103">Bir tür tanımının meta veri imzasını oluşturur, `mdTypeDef` Bu tür için bir belirteç döndürür ve tanımlı türün parametre tarafından başvurulan türün bir üyesi olduğunu belirtir `tdEncloser` .</span><span class="sxs-lookup"><span data-stu-id="41483-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41483-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="41483-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="41483-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41483-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="41483-106">'ndaki Unicode 'daki türün adı.</span><span class="sxs-lookup"><span data-stu-id="41483-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="41483-107">[in] `TypeDef` özelliklerine.</span><span class="sxs-lookup"><span data-stu-id="41483-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="41483-108">Bu bir değer bit değeridir `CorTypeAttr` .</span><span class="sxs-lookup"><span data-stu-id="41483-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="41483-109">'ndaki Taban sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="41483-109">[in] The token of the base class.</span></span> <span data-ttu-id="41483-110">Bu bir ya da `mdTypeDef` bir `mdTypeRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="41483-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="41483-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="41483-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="41483-112">'ndaki Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="41483-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="41483-113">'ndaki Kapsayan türün belirteci.</span><span class="sxs-lookup"><span data-stu-id="41483-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="41483-114">Dizinin son öğesi olmalıdır `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="41483-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="41483-115">dışı `mdTypeDef`Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="41483-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41483-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41483-116">Requirements</span></span>  
 <span data-ttu-id="41483-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41483-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41483-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="41483-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41483-119">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="41483-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41483-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41483-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41483-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41483-121">See also</span></span>

- [<span data-ttu-id="41483-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41483-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="41483-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41483-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

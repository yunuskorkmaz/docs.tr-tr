---
description: ': Imetadatayayma::D efineNestedType yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 1b0c5c8d1bffa425b2019a4434042c84a0069907
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753386"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="70796-103">IMetaDataEmit::DefineNestedType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70796-103">IMetaDataEmit::DefineNestedType Method</span></span>

<span data-ttu-id="70796-104">Bir tür tanımının meta veri imzasını oluşturur, `mdTypeDef` Bu tür için bir belirteç döndürür ve tanımlı türün parametre tarafından başvurulan türün bir üyesi olduğunu belirtir `tdEncloser` .</span><span class="sxs-lookup"><span data-stu-id="70796-104">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70796-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70796-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="70796-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70796-106">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="70796-107">'ndaki Unicode 'daki türün adı.</span><span class="sxs-lookup"><span data-stu-id="70796-107">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="70796-108">[in] `TypeDef` özelliklerine.</span><span class="sxs-lookup"><span data-stu-id="70796-108">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="70796-109">Bu bir değer bit değeridir `CorTypeAttr` .</span><span class="sxs-lookup"><span data-stu-id="70796-109">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="70796-110">'ndaki Taban sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="70796-110">[in] The token of the base class.</span></span> <span data-ttu-id="70796-111">Bu bir ya da `mdTypeDef` bir `mdTypeRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="70796-111">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="70796-112">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="70796-112">`rtkImplements`[]</span></span>  
 <span data-ttu-id="70796-113">'ndaki Bu sınıfın veya arabirimin uyguladığı arabirimleri belirten bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="70796-113">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="70796-114">'ndaki Kapsayan türün belirteci.</span><span class="sxs-lookup"><span data-stu-id="70796-114">[in] The token of the enclosing type.</span></span> <span data-ttu-id="70796-115">Dizinin son öğesi olmalıdır `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="70796-115">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="70796-116">dışı `mdTypeDef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="70796-116">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70796-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70796-117">Requirements</span></span>  

 <span data-ttu-id="70796-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70796-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70796-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="70796-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70796-120">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="70796-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70796-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70796-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70796-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70796-122">See also</span></span>

- [<span data-ttu-id="70796-123">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70796-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="70796-124">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70796-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

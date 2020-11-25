---
title: IMetaDataEmit::SetTypeDefProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: 2f572f66f16ff701350fde3b05be822b9e8c78b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706840"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="4dce0-102">IMetaDataEmit::SetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4dce0-102">IMetaDataEmit::SetTypeDefProps Method</span></span>

<span data-ttu-id="4dce0-103">[Imetadatayay::D efinetypedef](imetadataemit-definetypedef-method.md)önceki çağrısıyla tanımlanan bir türün özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4dce0-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dce0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4dce0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dce0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4dce0-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="4dce0-106">'ndaki `mdTypeDef` Özgün [ımetadatayay](imetadataemit-definetypedef-method.md)çağrısından alınan bir belirteç::D efinetypedef.</span><span class="sxs-lookup"><span data-stu-id="4dce0-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="4dce0-107">[in] `TypeDef` özelliklerine.</span><span class="sxs-lookup"><span data-stu-id="4dce0-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="4dce0-108">Bu bir değer bit değeridir `CorTypeAttr` .</span><span class="sxs-lookup"><span data-stu-id="4dce0-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="4dce0-109">'ndaki `mdToken` Temel sınıfın.</span><span class="sxs-lookup"><span data-stu-id="4dce0-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="4dce0-110">Imetadatayayma için önceki bir çağrıdan alındı [::D Efineımporttype](imetadataemit-defineimporttype-method.md)veya `null` .</span><span class="sxs-lookup"><span data-stu-id="4dce0-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="4dce0-111">'ndaki Bu türün uyguladığı arabirimler için bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="4dce0-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="4dce0-112">Bu `mdTypeRef` belirteçler [ımetadatayayma::D Efineımporttype](imetadataemit-defineimporttype-method.md)kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="4dce0-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="4dce0-113">Dizinin son öğesi olmalıdır `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="4dce0-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dce0-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4dce0-114">Requirements</span></span>  

 <span data-ttu-id="4dce0-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dce0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dce0-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4dce0-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4dce0-117">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4dce0-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dce0-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dce0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dce0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dce0-119">See also</span></span>

- [<span data-ttu-id="4dce0-120">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4dce0-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4dce0-121">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4dce0-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

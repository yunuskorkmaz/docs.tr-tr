---
description: ': Imetadatayayma:: SetTypeDefProps Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1160d20e7ceb422390f8cd725a75fdb4f42318e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706506"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="e5682-103">IMetaDataEmit::SetTypeDefProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5682-103">IMetaDataEmit::SetTypeDefProps Method</span></span>

<span data-ttu-id="e5682-104">[Imetadatayay::D efinetypedef](imetadataemit-definetypedef-method.md)önceki çağrısıyla tanımlanan bir türün özelliklerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e5682-104">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5682-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5682-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5682-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5682-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="e5682-107">'ndaki `mdTypeDef` Özgün [ımetadatayay](imetadataemit-definetypedef-method.md)çağrısından alınan bir belirteç::D efinetypedef.</span><span class="sxs-lookup"><span data-stu-id="e5682-107">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="e5682-108">[in] `TypeDef` özelliklerine.</span><span class="sxs-lookup"><span data-stu-id="e5682-108">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="e5682-109">Bu bir değer bit değeridir `CorTypeAttr` .</span><span class="sxs-lookup"><span data-stu-id="e5682-109">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="e5682-110">'ndaki `mdToken` Temel sınıfın.</span><span class="sxs-lookup"><span data-stu-id="e5682-110">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="e5682-111">Imetadatayayma için önceki bir çağrıdan alındı [::D Efineımporttype](imetadataemit-defineimporttype-method.md)veya `null` .</span><span class="sxs-lookup"><span data-stu-id="e5682-111">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="e5682-112">'ndaki Bu türün uyguladığı arabirimler için bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="e5682-112">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="e5682-113">Bu `mdTypeRef` belirteçler [ımetadatayayma::D Efineımporttype](imetadataemit-defineimporttype-method.md)kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="e5682-113">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="e5682-114">Dizinin son öğesi olmalıdır `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="e5682-114">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5682-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5682-115">Requirements</span></span>  

 <span data-ttu-id="e5682-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5682-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5682-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e5682-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5682-118">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e5682-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5682-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5682-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5682-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5682-120">See also</span></span>

- [<span data-ttu-id="e5682-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5682-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e5682-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5682-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

---
title: IMetaDataEmit::SetClassLayout Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type:
- apiref
ms.openlocfilehash: 5214298c6ad9594548ab45ed583cb5b14ce1f30d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441770"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="11f7f-102">IMetaDataEmit::SetClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11f7f-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="11f7f-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="11f7f-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f7f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11f7f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11f7f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11f7f-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="11f7f-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span><span class="sxs-lookup"><span data-stu-id="11f7f-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="11f7f-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span><span class="sxs-lookup"><span data-stu-id="11f7f-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="11f7f-108">The packing size is the number of bytes between adjacent fields.</span><span class="sxs-lookup"><span data-stu-id="11f7f-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="11f7f-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span><span class="sxs-lookup"><span data-stu-id="11f7f-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="11f7f-110">Terminate the array with `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="11f7f-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="11f7f-111">[in] The size, in bytes, of the class.</span><span class="sxs-lookup"><span data-stu-id="11f7f-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11f7f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11f7f-112">Remarks</span></span>  
 <span data-ttu-id="11f7f-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span><span class="sxs-lookup"><span data-stu-id="11f7f-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="11f7f-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span><span class="sxs-lookup"><span data-stu-id="11f7f-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="11f7f-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span><span class="sxs-lookup"><span data-stu-id="11f7f-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="11f7f-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span><span class="sxs-lookup"><span data-stu-id="11f7f-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="11f7f-117">Sequential layout: Specify the packing size.</span><span class="sxs-lookup"><span data-stu-id="11f7f-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="11f7f-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span><span class="sxs-lookup"><span data-stu-id="11f7f-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="11f7f-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span><span class="sxs-lookup"><span data-stu-id="11f7f-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="11f7f-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span><span class="sxs-lookup"><span data-stu-id="11f7f-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11f7f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11f7f-121">Requirements</span></span>  
 <span data-ttu-id="11f7f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11f7f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11f7f-123">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11f7f-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11f7f-124">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11f7f-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11f7f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11f7f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f7f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11f7f-126">See also</span></span>

- [<span data-ttu-id="11f7f-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11f7f-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="11f7f-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11f7f-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

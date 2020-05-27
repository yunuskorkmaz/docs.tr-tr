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
ms.openlocfilehash: a18583ce807ffa672811f3a0cd1e744233f6eb30
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008839"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="3cce8-102">IMetaDataEmit::SetClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cce8-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="3cce8-103">Önceki bir [DefineTypeDef yöntemi](imetadataemit-definetypedef-method.md)çağrısıyla tanımlanmış bir sınıf için alanların yerleşimini tamamlar.</span><span class="sxs-lookup"><span data-stu-id="3cce8-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cce8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3cce8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cce8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cce8-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3cce8-106">'ndaki `mdTypeDef`Çıkarılacak sınıfı belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="3cce8-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="3cce8-107">'ndaki Paketleme boyutu: 1, 2, 4, 8 veya 16 bayt.</span><span class="sxs-lookup"><span data-stu-id="3cce8-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="3cce8-108">Paketleme boyutu bitişik alanlar arasındaki baytların sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="3cce8-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="3cce8-109">'ndaki Her biri sınıfının bir alanını ve alanın içindeki sapmasını belirten [COR_FIELD_OFFSET](cor-field-offset-structure.md) yapılarının bir dizisi.</span><span class="sxs-lookup"><span data-stu-id="3cce8-109">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="3cce8-110">Diziyi ile sonlandırın `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="3cce8-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="3cce8-111">'ndaki Sınıfın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="3cce8-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cce8-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cce8-112">Remarks</span></span>  
 <span data-ttu-id="3cce8-113">Sınıfı ilk olarak [ımetadatayayma::D efinetypedef](imetadataemit-definetypedef-method.md) yöntemi çağırarak ve sınıfın alanları için üç düzenden birini belirterek tanımlanır: otomatik, sıralı veya açık.</span><span class="sxs-lookup"><span data-stu-id="3cce8-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="3cce8-114">Normal olarak, Otomatik düzeni kullanır ve çalışma zamanının alanları düzenlemenin en iyi yolunu seçmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cce8-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="3cce8-115">Ancak, alanların yönetilmeyen kodun kullandığı düzenlemeye göre yerleşimini tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cce8-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="3cce8-116">Bu durumda, `SetClassLayout` alanların yerleşimini tamamlamaya yönelik sıralı ya da açık Düzen ' i ve çağrı ' yı seçin:</span><span class="sxs-lookup"><span data-stu-id="3cce8-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="3cce8-117">Sıralı Düzen: paketleme boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="3cce8-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="3cce8-118">Bir alan doğal boyutuna veya paketleme boyutuna göre hizalanır ve bu da alanın daha küçük bir uzaklığa neden olur.</span><span class="sxs-lookup"><span data-stu-id="3cce8-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="3cce8-119">`rFieldOffsets`Ve öğesini `ulClassSize` sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3cce8-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="3cce8-120">Açık Düzen: her alanın sapmasını belirtin ya da sınıf boyutunu ve paketleme boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="3cce8-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cce8-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cce8-121">Requirements</span></span>  
 <span data-ttu-id="3cce8-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cce8-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cce8-123">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3cce8-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3cce8-124">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3cce8-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cce8-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cce8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cce8-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cce8-126">See also</span></span>

- [<span data-ttu-id="3cce8-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cce8-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3cce8-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cce8-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

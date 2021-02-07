---
description: ': Imetadatayayma:: SetClassLayout yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e0ce8e93137b9a32a13ca86ead539385523fa8a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706610"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="ad8a5-103">IMetaDataEmit::SetClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad8a5-103">IMetaDataEmit::SetClassLayout Method</span></span>

<span data-ttu-id="ad8a5-104">Önceki bir [DefineTypeDef yöntemi](imetadataemit-definetypedef-method.md)çağrısıyla tanımlanmış bir sınıf için alanların yerleşimini tamamlar.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-104">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad8a5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad8a5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad8a5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad8a5-106">Parameters</span></span>  

 `td`  
 <span data-ttu-id="ad8a5-107">'ndaki `mdTypeDef` Çıkarılacak sınıfı belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-107">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="ad8a5-108">'ndaki Paketleme boyutu: 1, 2, 4, 8 veya 16 bayt.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-108">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="ad8a5-109">Paketleme boyutu bitişik alanlar arasındaki baytların sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-109">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="ad8a5-110">'ndaki Her biri sınıfının bir alanını ve alanın içindeki sapmasını belirten [COR_FIELD_OFFSET](cor-field-offset-structure.md) yapılarının bir dizisi.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-110">[in] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="ad8a5-111">Diziyi ile sonlandırın `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="ad8a5-111">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="ad8a5-112">'ndaki Sınıfın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-112">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad8a5-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad8a5-113">Remarks</span></span>  

 <span data-ttu-id="ad8a5-114">Sınıfı ilk olarak [ımetadatayayma::D efinetypedef](imetadataemit-definetypedef-method.md) yöntemi çağırarak ve sınıfın alanları için üç düzenden birini belirterek tanımlanır: otomatik, sıralı veya açık.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-114">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="ad8a5-115">Normal olarak, Otomatik düzeni kullanır ve çalışma zamanının alanları düzenlemenin en iyi yolunu seçmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-115">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="ad8a5-116">Ancak, alanların yönetilmeyen kodun kullandığı düzenlemeye göre yerleşimini tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-116">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="ad8a5-117">Bu durumda, `SetClassLayout` alanların yerleşimini tamamlamaya yönelik sıralı ya da açık Düzen ' i ve çağrı ' yı seçin:</span><span class="sxs-lookup"><span data-stu-id="ad8a5-117">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="ad8a5-118">Sıralı Düzen: paketleme boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-118">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="ad8a5-119">Bir alan doğal boyutuna veya paketleme boyutuna göre hizalanır ve bu da alanın daha küçük bir uzaklığa neden olur.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-119">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="ad8a5-120">`rFieldOffsets`Ve öğesini `ulClassSize` sıfır olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-120">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="ad8a5-121">Açık Düzen: her alanın sapmasını belirtin ya da sınıf boyutunu ve paketleme boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-121">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad8a5-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad8a5-122">Requirements</span></span>  

 <span data-ttu-id="ad8a5-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad8a5-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad8a5-124">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ad8a5-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad8a5-125">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ad8a5-125">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad8a5-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad8a5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8a5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad8a5-127">See also</span></span>

- [<span data-ttu-id="ad8a5-128">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad8a5-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ad8a5-129">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad8a5-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

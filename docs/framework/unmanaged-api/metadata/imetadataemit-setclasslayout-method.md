---
title: "IMetaDataEmit::SetClassLayout Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0c02e615bf77a2cc9136b50efd7395585959141
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="cfa11-102">IMetaDataEmit::SetClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfa11-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="cfa11-103">Önceki bir çağrı tarafından tanımlanan bir sınıf için alanlarının düzenini tamamlandıktan [DefineTypeDef yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="cfa11-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa11-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfa11-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfa11-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfa11-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="cfa11-106">[in] Bir `mdTypeDef` düzenlendiği için sınıf belirtir belirteci.</span><span class="sxs-lookup"><span data-stu-id="cfa11-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="cfa11-107">[in] Paket boyutu: 1, 2, 4, 8 veya 16 bayt.</span><span class="sxs-lookup"><span data-stu-id="cfa11-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="cfa11-108">Paket boyutu bitişik alanlar arasında bayt sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="cfa11-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="cfa11-109">[in] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları, her biri belirtir sınıfının bir alanı ve alan sınıf içinde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="cfa11-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="cfa11-110">Dizi ile sonlandırmak `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="cfa11-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="cfa11-111">[in] Sınıfının bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="cfa11-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfa11-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfa11-112">Remarks</span></span>  
 <span data-ttu-id="cfa11-113">Sınıfı, başlangıçta çağırarak tanımlanır [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemi ve sınıfın alanları için üç düzenleri birini belirterek: otomatik, sıralı ya da açık.</span><span class="sxs-lookup"><span data-stu-id="cfa11-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="cfa11-114">Normalde, otomatik düzenini kullanın ve alanları düzenlemek için en iyi yolu seçin çalışma zamanı izin.</span><span class="sxs-lookup"><span data-stu-id="cfa11-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="cfa11-115">Bununla birlikte, kod kullandığı yönetilmeyen düzenlemeyi göre yerleştirilmiş normal bir kutudur alanları isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfa11-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="cfa11-116">Bu durumda, sıralı veya açık düzenini çağrısı seçip `SetClassLayout` alanlarının düzenini tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="cfa11-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="cfa11-117">Ardışık Düzen: paket boyutu belirtin.</span><span class="sxs-lookup"><span data-stu-id="cfa11-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="cfa11-118">Bir alan doğal boyutu veya paket boyutu, alan daha küçük uzaklığını hangi sonuçlarında göre hizalanır.</span><span class="sxs-lookup"><span data-stu-id="cfa11-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="cfa11-119">Ayarlama `rFieldOffsets` ve `ulClassSize` sıfır.</span><span class="sxs-lookup"><span data-stu-id="cfa11-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="cfa11-120">Açık düzene: her bir alan uzaklığını ya da sınıf boyutu ve paket boyutu belirtin.</span><span class="sxs-lookup"><span data-stu-id="cfa11-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa11-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfa11-121">Requirements</span></span>  
 <span data-ttu-id="cfa11-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfa11-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfa11-123">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cfa11-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cfa11-124">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cfa11-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cfa11-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfa11-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa11-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cfa11-126">See Also</span></span>  
 [<span data-ttu-id="cfa11-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa11-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="cfa11-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa11-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

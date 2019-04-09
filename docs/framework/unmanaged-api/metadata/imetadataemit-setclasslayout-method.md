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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bf9de3eb274bf536b2794ba2ed14e7e9b553cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157709"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="bba82-102">IMetaDataEmit::SetClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bba82-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="bba82-103">Önceki bir çağrı tarafından tanımlanan bir sınıf için alanlarının düzenini tamamlandıktan [DefineTypeDef yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="bba82-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bba82-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bba82-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bba82-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="bba82-106">[in] Bir `mdTypeDef` belirteci dışı sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bba82-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="bba82-107">[in] Paketleme boyutu: 1, 2, 4, 8 veya 16 bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="bba82-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="bba82-108">Bitişik alanları arasında bulunan bayt sayısını paketleme boyutudur.</span><span class="sxs-lookup"><span data-stu-id="bba82-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="bba82-109">[in] Bir dizi [cor_fıeld_offset](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları, her biri belirtir sınıfının bir alanı ve alan içindeki sınıf uzaklığını.</span><span class="sxs-lookup"><span data-stu-id="bba82-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="bba82-110">Dizi sonlandırmak `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="bba82-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="bba82-111">[in] Sınıf bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="bba82-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bba82-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bba82-112">Remarks</span></span>  
 <span data-ttu-id="bba82-113">Sınıfı, başlangıçta çağırarak tanımlanır [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemi ve sınıf alanlar için üç düzenlerden birini belirterek: otomatik, sıralı ya da açık.</span><span class="sxs-lookup"><span data-stu-id="bba82-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="bba82-114">Normalde, otomatik düzeni kullanma ve alanları düzenlemek için en iyi yolu seçin çalışma zamanının.</span><span class="sxs-lookup"><span data-stu-id="bba82-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="bba82-115">Ancak, kodunuz yönetilmeyen düzenleme göre düzenlendiği alanları isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bba82-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="bba82-116">Bu durumda, doğrudan ya da ardışık düzen ve çağrı seçin `SetClassLayout` alanlarının düzenini tamamlamak için:</span><span class="sxs-lookup"><span data-stu-id="bba82-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="bba82-117">Ardışık Düzen: Paketleme boyutu belirtin.</span><span class="sxs-lookup"><span data-stu-id="bba82-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="bba82-118">Alana göre doğal boyutu veya paketleme boyutu, hangi alanın daha küçük uzaklığı sonuçlarında hizalanır.</span><span class="sxs-lookup"><span data-stu-id="bba82-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="bba82-119">Ayarlama `rFieldOffsets` ve `ulClassSize` sıfır.</span><span class="sxs-lookup"><span data-stu-id="bba82-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="bba82-120">Açık düzeni: Her alanın bir uzaklık belirtin ya da sınıf boyutu ve paketleme boyutu belirtin.</span><span class="sxs-lookup"><span data-stu-id="bba82-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bba82-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bba82-121">Requirements</span></span>  
 <span data-ttu-id="bba82-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bba82-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bba82-123">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bba82-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bba82-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="bba82-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="bba82-125">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bba82-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bba82-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bba82-126">See also</span></span>

- [<span data-ttu-id="bba82-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bba82-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bba82-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bba82-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

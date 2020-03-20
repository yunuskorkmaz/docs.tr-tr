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
ms.openlocfilehash: e855868d18fc6cffdd5d92cfa401606caf45b76c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177570"
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="44ebc-102">IMetaDataEmit::SetClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44ebc-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="44ebc-103">[DefineTypeDef Yöntemi'ne](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)önceki bir çağrıyla tanımlanan bir sınıfın alanlarının düzenini tamamlar.</span><span class="sxs-lookup"><span data-stu-id="44ebc-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44ebc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44ebc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,
    [in]  DWORD               dwPackSize,
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],
    [in]  ULONG               ulClassSize
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44ebc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44ebc-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="44ebc-106">[içinde] Ortaya `mdTypeDef` konacak sınıfı belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="44ebc-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="44ebc-107">[içinde] Ambalaj boyutu: 1, 2, 4, 8 veya 16 bayt.</span><span class="sxs-lookup"><span data-stu-id="44ebc-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="44ebc-108">Paketleme boyutu, bitişik alanlar arasındaki bayt sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="44ebc-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="44ebc-109">[içinde] Her biri sınıfın bir alanını ve sınıfın içindeki alanın ofsetini belirten [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="44ebc-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="44ebc-110">Diziyi `mdTokenNil`' ile sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="44ebc-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="44ebc-111">[içinde] Sınıfın büyüklüğü, baytlar halinde.</span><span class="sxs-lookup"><span data-stu-id="44ebc-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44ebc-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44ebc-112">Remarks</span></span>  
 <span data-ttu-id="44ebc-113">Sınıf başlangıçta [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) yöntemini çağırarak ve sınıfın alanları için üç düzenden birini belirterek tanımlanır: otomatik, sıralı veya açık.</span><span class="sxs-lookup"><span data-stu-id="44ebc-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="44ebc-114">Normalde, otomatik düzeni kullanır ve çalışma zamanı alanları düzenlemek için en iyi yolu seçmesine izin.</span><span class="sxs-lookup"><span data-stu-id="44ebc-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="44ebc-115">Ancak, yönetilmeyen kodun kullandığı düzenlemeye göre alanların düzenlenmesini isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44ebc-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="44ebc-116">Bu durumda, alanların düzenini tamamlamak `SetClassLayout` için sıralı veya açık düzeni seçin ve arayın:</span><span class="sxs-lookup"><span data-stu-id="44ebc-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
- <span data-ttu-id="44ebc-117">Sıralı düzen: Ambalaj boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="44ebc-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="44ebc-118">Bir alan, alanın daha küçük ofset ile sonuçlandığı doğal boyutuna veya ambalaj boyutuna göre hizalanır.</span><span class="sxs-lookup"><span data-stu-id="44ebc-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="44ebc-119">Ayarlayın `rFieldOffsets` `ulClassSize` ve sıfıra ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="44ebc-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
- <span data-ttu-id="44ebc-120">Açık düzen: Her alanın mahsupını belirtin veya sınıf boyutunu ve ambalaj boyutunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="44ebc-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44ebc-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44ebc-121">Requirements</span></span>  
 <span data-ttu-id="44ebc-122">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44ebc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44ebc-123">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="44ebc-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44ebc-124">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="44ebc-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44ebc-125">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44ebc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ebc-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44ebc-126">See also</span></span>

- [<span data-ttu-id="44ebc-127">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44ebc-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="44ebc-128">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44ebc-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

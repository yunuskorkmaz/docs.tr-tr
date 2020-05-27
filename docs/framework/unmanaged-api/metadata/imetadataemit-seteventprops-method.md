---
title: IMetaDataEmit::SetEventProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008761"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="73777-102">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73777-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="73777-103">[Imetadatayayma::D efineEvent](imetadataemit-defineevent-method.md)için önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="73777-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73777-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="73777-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73777-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73777-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="73777-106">'ndaki Olay belirteci.</span><span class="sxs-lookup"><span data-stu-id="73777-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="73777-107">'ndaki Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="73777-107">[in] Event flags.</span></span> <span data-ttu-id="73777-108">Bu bir değer bit değeridir `CorEventAttr` .</span><span class="sxs-lookup"><span data-stu-id="73777-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="73777-109">'ndaki Olay sınıfı için belirteç.</span><span class="sxs-lookup"><span data-stu-id="73777-109">[in] The token for the event class.</span></span> <span data-ttu-id="73777-110">Bu bir ya da `mdTypeDef` bir `mdTypeRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="73777-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="73777-111">'ndaki Olaya abone olmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="73777-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="73777-112">'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="73777-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="73777-113">'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).</span><span class="sxs-lookup"><span data-stu-id="73777-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="73777-114">'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="73777-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="73777-115">Dizinin son öğesi olmalıdır `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="73777-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73777-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73777-116">Requirements</span></span>  
 <span data-ttu-id="73777-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73777-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73777-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="73777-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="73777-119">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="73777-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73777-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73777-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73777-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73777-121">See also</span></span>

- [<span data-ttu-id="73777-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73777-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="73777-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73777-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

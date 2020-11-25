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
ms.openlocfilehash: 5c2880ac07f0317bc36ff4bbde68cd3a25febf52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721991"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="a1d1a-102">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1d1a-102">IMetaDataEmit::SetEventProps Method</span></span>

<span data-ttu-id="a1d1a-103">[Imetadatayayma::D efineEvent](imetadataemit-defineevent-method.md)için önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1d1a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a1d1a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a1d1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1d1a-105">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="a1d1a-106">'ndaki Olay belirteci.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="a1d1a-107">'ndaki Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-107">[in] Event flags.</span></span> <span data-ttu-id="a1d1a-108">Bu bir değer bit değeridir `CorEventAttr` .</span><span class="sxs-lookup"><span data-stu-id="a1d1a-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="a1d1a-109">'ndaki Olay sınıfı için belirteç.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-109">[in] The token for the event class.</span></span> <span data-ttu-id="a1d1a-110">Bu bir ya da `mdTypeDef` bir `mdTypeRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="a1d1a-111">'ndaki Olaya abone olmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="a1d1a-112">'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="a1d1a-113">'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).</span><span class="sxs-lookup"><span data-stu-id="a1d1a-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="a1d1a-114">'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="a1d1a-115">Dizinin son öğesi olmalıdır `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="a1d1a-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1d1a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1d1a-116">Requirements</span></span>  

 <span data-ttu-id="a1d1a-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1d1a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1d1a-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a1d1a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1d1a-119">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a1d1a-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1d1a-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1d1a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d1a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d1a-121">See also</span></span>

- [<span data-ttu-id="a1d1a-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1d1a-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a1d1a-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1d1a-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

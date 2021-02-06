---
description: ': Imetadatayayma:: SetEventProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 888999bc0f80e82e0d139eecac7152a94104ed7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658138"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="4ab91-103">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4ab91-103">IMetaDataEmit::SetEventProps Method</span></span>

<span data-ttu-id="4ab91-104">[Imetadatayayma::D efineEvent](imetadataemit-defineevent-method.md)için önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="4ab91-104">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab91-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ab91-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4ab91-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ab91-106">Parameters</span></span>  

 `ev`  
 <span data-ttu-id="4ab91-107">'ndaki Olay belirteci.</span><span class="sxs-lookup"><span data-stu-id="4ab91-107">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="4ab91-108">'ndaki Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="4ab91-108">[in] Event flags.</span></span> <span data-ttu-id="4ab91-109">Bu bir değer bit değeridir `CorEventAttr` .</span><span class="sxs-lookup"><span data-stu-id="4ab91-109">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="4ab91-110">'ndaki Olay sınıfı için belirteç.</span><span class="sxs-lookup"><span data-stu-id="4ab91-110">[in] The token for the event class.</span></span> <span data-ttu-id="4ab91-111">Bu bir ya da `mdTypeDef` bir `mdTypeRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="4ab91-111">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="4ab91-112">'ndaki Olaya abone olmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="4ab91-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="4ab91-113">'ndaki Olayın aboneliğini kaldırmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="4ab91-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="4ab91-114">'ndaki Olayı yükseltmek için kullanılan Yöntem (türetilmiş bir sınıf tarafından).</span><span class="sxs-lookup"><span data-stu-id="4ab91-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="4ab91-115">'ndaki Olayla ilişkili diğer yöntemler için bir belirteç dizisi.</span><span class="sxs-lookup"><span data-stu-id="4ab91-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="4ab91-116">Dizinin son öğesi olmalıdır `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="4ab91-116">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ab91-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ab91-117">Requirements</span></span>  

 <span data-ttu-id="4ab91-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ab91-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab91-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4ab91-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ab91-120">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4ab91-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ab91-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab91-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab91-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ab91-122">See also</span></span>

- [<span data-ttu-id="4ab91-123">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ab91-123">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4ab91-124">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ab91-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

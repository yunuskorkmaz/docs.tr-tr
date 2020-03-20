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
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177524"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="1469b-102">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1469b-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="1469b-103">[IMetaDataEmit::DefineEvent'e](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)yapılan bir önceki çağrıyla tanımlanan bir olayın belirtilen özelliğini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1469b-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1469b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1469b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1469b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1469b-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="1469b-106">[içinde] Olay belirteci.</span><span class="sxs-lookup"><span data-stu-id="1469b-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="1469b-107">[içinde] Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="1469b-107">[in] Event flags.</span></span> <span data-ttu-id="1469b-108">Bu `CorEventAttr` değerlerin bir bitmask olduğunu.</span><span class="sxs-lookup"><span data-stu-id="1469b-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="1469b-109">[içinde] Olay sınıfının belirteci.</span><span class="sxs-lookup"><span data-stu-id="1469b-109">[in] The token for the event class.</span></span> <span data-ttu-id="1469b-110">Bu ya `mdTypeDef` bir `mdTypeRef` ya da bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="1469b-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="1469b-111">[içinde] Olaya abone olmak için kullanılan yöntem veya null.</span><span class="sxs-lookup"><span data-stu-id="1469b-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="1469b-112">[içinde] Olaya aboneliğini iptal etmek veya geçersiz kılmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="1469b-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="1469b-113">[içinde] Olayı yükseltmek için (türetilmiş bir sınıf tarafından) kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="1469b-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="1469b-114">[içinde] Olayla ilişkili diğer yöntemler için bir dizi belirteç.</span><span class="sxs-lookup"><span data-stu-id="1469b-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="1469b-115">Dizinin son öğesi `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="1469b-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1469b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1469b-116">Requirements</span></span>  
 <span data-ttu-id="1469b-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1469b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1469b-118">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1469b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1469b-119">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1469b-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1469b-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1469b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1469b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1469b-121">See also</span></span>

- [<span data-ttu-id="1469b-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1469b-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1469b-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1469b-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

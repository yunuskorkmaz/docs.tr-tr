---
title: "IMetaDataEmit::DefineEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf790ce270565abaf1d91e54c9e3569a50ab3435
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="359ae-102">IMetaDataEmit::DefineEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="359ae-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="359ae-103">Belirtilen meta veri imzayla bir olay için bir tanım oluşturur ve bu olay tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="359ae-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="359ae-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="359ae-104">Syntax</span></span>  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="359ae-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="359ae-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="359ae-106">[in] Hedef sınıf veya arabirim için belirteci.</span><span class="sxs-lookup"><span data-stu-id="359ae-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="359ae-107">Bu olan bir `mdTypeDef` veya `mdTypeDefNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="359ae-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="359ae-108">[in] Olayın adı.</span><span class="sxs-lookup"><span data-stu-id="359ae-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="359ae-109">[in] Olay bayraklar.</span><span class="sxs-lookup"><span data-stu-id="359ae-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="359ae-110">[in] Event sınıfı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="359ae-110">[in] The token for the event class.</span></span> <span data-ttu-id="359ae-111">Bu bir `mdTypeDef`, `mdTypeRef`, veya bir `mdTokenNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="359ae-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="359ae-112">[in] Olay ya da null için abone olmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="359ae-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="359ae-113">[in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="359ae-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="359ae-114">[in] (Türetilmiş sınıf tarafından) olay yükseltmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="359ae-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="359ae-115">[in] Olayla ilişkili diğer yöntemleri için belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="359ae-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="359ae-116">Dizi ile sonlandırılan bir `mdMethodDefNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="359ae-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="359ae-117">[out] Olaya atanan meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="359ae-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="359ae-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="359ae-118">Requirements</span></span>  
 <span data-ttu-id="359ae-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="359ae-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="359ae-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="359ae-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="359ae-121">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="359ae-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="359ae-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="359ae-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359ae-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="359ae-123">See Also</span></span>  
 [<span data-ttu-id="359ae-124">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="359ae-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="359ae-125">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="359ae-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

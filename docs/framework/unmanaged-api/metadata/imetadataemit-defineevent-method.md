---
title: "IMetaDataEmit::DefineEvent Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f27c0a01dd795cfcc5399c4115cd6d905629fd7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="47f60-102">IMetaDataEmit::DefineEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47f60-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="47f60-103">Belirtilen meta veri imzayla bir olay için bir tanım oluşturur ve bu olay tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="47f60-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47f60-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47f60-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="47f60-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47f60-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="47f60-106">[in] Hedef sınıf veya arabirim için belirteci.</span><span class="sxs-lookup"><span data-stu-id="47f60-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="47f60-107">Bu olan bir `mdTypeDef` veya `mdTypeDefNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="47f60-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="47f60-108">[in] Olayın adı.</span><span class="sxs-lookup"><span data-stu-id="47f60-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="47f60-109">[in] Olay bayraklar.</span><span class="sxs-lookup"><span data-stu-id="47f60-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="47f60-110">[in] Event sınıfı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="47f60-110">[in] The token for the event class.</span></span> <span data-ttu-id="47f60-111">Bu bir `mdTypeDef`, `mdTypeRef`, veya bir `mdTokenNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="47f60-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="47f60-112">[in] Olay ya da null için abone olmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="47f60-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="47f60-113">[in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="47f60-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="47f60-114">[in] (Türetilmiş sınıf tarafından) olay yükseltmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="47f60-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="47f60-115">[in] Olayla ilişkili diğer yöntemleri için belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="47f60-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="47f60-116">Dizi ile sonlandırılan bir `mdMethodDefNil` belirteci.</span><span class="sxs-lookup"><span data-stu-id="47f60-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="47f60-117">[out] Olaya atanan meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="47f60-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47f60-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47f60-118">Requirements</span></span>  
 <span data-ttu-id="47f60-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47f60-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47f60-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="47f60-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47f60-121">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="47f60-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47f60-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47f60-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47f60-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47f60-123">See Also</span></span>  
 [<span data-ttu-id="47f60-124">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47f60-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="47f60-125">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47f60-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

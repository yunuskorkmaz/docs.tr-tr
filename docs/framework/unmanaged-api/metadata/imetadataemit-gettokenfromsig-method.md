---
title: IMetaDataEmit::GetTokenFromSig Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetTokenFromSig
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aefd95f62fce70f87c0724cbb4013462a449c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="b96cd-102">IMetaDataEmit::GetTokenFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="b96cd-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="b96cd-103">Belirtilen meta veri imza için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="b96cd-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b96cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b96cd-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b96cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b96cd-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="b96cd-106">[in] Kalıcı ve depolanacak imzası.</span><span class="sxs-lookup"><span data-stu-id="b96cd-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="b96cd-107">[in] Bayt sayısı `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="b96cd-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="b96cd-108">[out] `mdSignature` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="b96cd-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b96cd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b96cd-109">Requirements</span></span>  
 <span data-ttu-id="b96cd-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b96cd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b96cd-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b96cd-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b96cd-112">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b96cd-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b96cd-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b96cd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96cd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b96cd-114">See Also</span></span>  
 [<span data-ttu-id="b96cd-115">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="b96cd-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b96cd-116">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="b96cd-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

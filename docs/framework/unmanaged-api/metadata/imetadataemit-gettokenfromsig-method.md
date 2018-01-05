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
ms.workload: dotnet
ms.openlocfilehash: df454b8dd95839f4cabe3c725e206f3683437ec4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="deddb-102">IMetaDataEmit::GetTokenFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="deddb-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="deddb-103">Belirtilen meta veri imza için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="deddb-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deddb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="deddb-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="deddb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="deddb-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="deddb-106">[in] Kalıcı ve depolanacak imzası.</span><span class="sxs-lookup"><span data-stu-id="deddb-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="deddb-107">[in] Bayt sayısı `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="deddb-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="deddb-108">[out] `mdSignature` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="deddb-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deddb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="deddb-109">Requirements</span></span>  
 <span data-ttu-id="deddb-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deddb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deddb-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="deddb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="deddb-112">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="deddb-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="deddb-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deddb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deddb-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="deddb-114">See Also</span></span>  
 [<span data-ttu-id="deddb-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="deddb-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="deddb-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="deddb-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

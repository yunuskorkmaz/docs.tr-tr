---
title: IMetaDataEmit::GetTokenFromSig Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be42fea034be4fe5d48874b00db86977a3039a34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448226"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="3628b-102">IMetaDataEmit::GetTokenFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="3628b-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="3628b-103">Belirtilen meta veri imza için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="3628b-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3628b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3628b-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3628b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3628b-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="3628b-106">[in] Kalıcı ve depolanacak imzası.</span><span class="sxs-lookup"><span data-stu-id="3628b-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="3628b-107">[in] Bayt sayısı `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="3628b-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="3628b-108">[out] `mdSignature` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="3628b-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3628b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3628b-109">Requirements</span></span>  
 <span data-ttu-id="3628b-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3628b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3628b-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3628b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3628b-112">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3628b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3628b-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3628b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3628b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3628b-114">See Also</span></span>  
 [<span data-ttu-id="3628b-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3628b-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="3628b-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3628b-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

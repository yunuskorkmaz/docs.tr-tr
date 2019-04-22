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
ms.openlocfilehash: 242618fb2a5ab748132baf68e24240d1ffaf2301
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139847"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="3cc52-102">IMetaDataEmit::GetTokenFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="3cc52-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="3cc52-103">Belirtilen meta veri imzası bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="3cc52-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cc52-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cc52-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="3cc52-106">[in] Kalıcı ve depolanacak imzası.</span><span class="sxs-lookup"><span data-stu-id="3cc52-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="3cc52-107">[in] Bayt sayısı `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="3cc52-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="3cc52-108">[out] `mdSignature` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="3cc52-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc52-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cc52-109">Requirements</span></span>  
 <span data-ttu-id="3cc52-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cc52-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc52-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3cc52-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3cc52-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3cc52-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cc52-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc52-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc52-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cc52-114">See also</span></span>

- [<span data-ttu-id="3cc52-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cc52-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3cc52-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cc52-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

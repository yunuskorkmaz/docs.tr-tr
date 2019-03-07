---
title: IMetaDataEmit::GetTokenFromTypeSpec Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff240a80d2910dcb050cc022257c6eba166bbdc5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465939"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="6a20d-102">IMetaDataEmit::GetTokenFromTypeSpec Metodu</span><span class="sxs-lookup"><span data-stu-id="6a20d-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="6a20d-103">Bir meta veri türü belirtilen meta veri imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="6a20d-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a20d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a20d-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a20d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a20d-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="6a20d-106">[in] Tanımlanan imzası.</span><span class="sxs-lookup"><span data-stu-id="6a20d-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="6a20d-107">[in] Bayt sayısı `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="6a20d-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="6a20d-108">[out] `mdTypeSpec` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="6a20d-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a20d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a20d-109">Requirements</span></span>  
 <span data-ttu-id="6a20d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a20d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a20d-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6a20d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a20d-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="6a20d-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a20d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a20d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a20d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a20d-114">See also</span></span>
- [<span data-ttu-id="6a20d-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a20d-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6a20d-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a20d-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

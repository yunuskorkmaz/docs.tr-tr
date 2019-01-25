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
ms.openlocfilehash: d45f818c74204517a238e4c9d40ebd4fcd88b0f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641323"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="1230c-102">IMetaDataEmit::GetTokenFromTypeSpec Metodu</span><span class="sxs-lookup"><span data-stu-id="1230c-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="1230c-103">Bir meta veri türü belirtilen meta veri imzası belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="1230c-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1230c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1230c-104">Syntax</span></span>  
  
```  
HRESULT GetTokenFromTypeSpec (   
    [in]  PCCOR_SIGNATURE       pvSig,   
    [in]  ULONG                 cbSig,   
    [out] mdTypeSpec            *ptypespec   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1230c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1230c-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="1230c-106">[in] Tanımlanan imzası.</span><span class="sxs-lookup"><span data-stu-id="1230c-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="1230c-107">[in] Bayt sayısı `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="1230c-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="1230c-108">[out] `mdTypeSpec` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="1230c-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1230c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1230c-109">Requirements</span></span>  
 <span data-ttu-id="1230c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1230c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1230c-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1230c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1230c-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1230c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1230c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1230c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1230c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1230c-114">See also</span></span>
- [<span data-ttu-id="1230c-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1230c-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1230c-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1230c-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

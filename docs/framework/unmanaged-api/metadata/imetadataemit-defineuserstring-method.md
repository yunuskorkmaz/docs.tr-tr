---
title: "IMetaDataEmit::DefineUserString Yöntemi"
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
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 729f2d48722fb34b844636b416edf36d715e1a48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="6ff14-102">IMetaDataEmit::DefineUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ff14-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="6ff14-103">Bir meta veri için belirtilen değişmez değer dize belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="6ff14-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ff14-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ff14-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ff14-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ff14-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="6ff14-106">[in] Depolamak için kullanıcı dizesi.</span><span class="sxs-lookup"><span data-stu-id="6ff14-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="6ff14-107">[in] Geniş karakter sayısı `szString`.</span><span class="sxs-lookup"><span data-stu-id="6ff14-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="6ff14-108">[out] Atanan dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="6ff14-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ff14-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ff14-109">Requirements</span></span>  
 <span data-ttu-id="6ff14-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ff14-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ff14-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6ff14-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ff14-112">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6ff14-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ff14-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ff14-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ff14-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ff14-114">See Also</span></span>  
 [<span data-ttu-id="6ff14-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ff14-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6ff14-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ff14-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

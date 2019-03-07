---
title: IMetaDataEmit::SaveToMemory Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6e9bb51965b258093321a5dbb19447ec6d6474d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471834"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="a7d83-102">IMetaDataEmit::SaveToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7d83-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="a7d83-103">Belirtilen bellek alanına geçerli kapsamdaki tüm meta verileri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a7d83-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7d83-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7d83-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7d83-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7d83-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="a7d83-106">[out] Meta verileri yazarken başlanacak adresi.</span><span class="sxs-lookup"><span data-stu-id="a7d83-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="a7d83-107">[in] Ayrılan belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="a7d83-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7d83-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7d83-108">Requirements</span></span>  
 <span data-ttu-id="a7d83-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7d83-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7d83-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a7d83-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7d83-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="a7d83-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7d83-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7d83-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d83-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7d83-113">See also</span></span>
- [<span data-ttu-id="a7d83-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7d83-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a7d83-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7d83-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

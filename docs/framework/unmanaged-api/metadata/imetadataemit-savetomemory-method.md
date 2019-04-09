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
ms.openlocfilehash: bc840df9dd0793a7347b7f0d8a05296a09d634c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192114"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="faa96-102">IMetaDataEmit::SaveToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="faa96-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="faa96-103">Belirtilen bellek alanına geçerli kapsamdaki tüm meta verileri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="faa96-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="faa96-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faa96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="faa96-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="faa96-106">[out] Meta verileri yazarken başlanacak adresi.</span><span class="sxs-lookup"><span data-stu-id="faa96-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="faa96-107">[in] Ayrılan belleğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="faa96-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa96-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="faa96-108">Requirements</span></span>  
 <span data-ttu-id="faa96-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa96-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa96-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="faa96-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="faa96-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="faa96-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="faa96-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="faa96-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="faa96-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faa96-113">See also</span></span>

- [<span data-ttu-id="faa96-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="faa96-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="faa96-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="faa96-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

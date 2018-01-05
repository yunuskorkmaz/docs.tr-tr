---
title: "IMetaDataEmit2::SaveDeltaToMemory Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDeltaToMemory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4243840ac64a14b4f4e6c86787fdf238507635
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="667a8-102">IMetaDataEmit2::SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="667a8-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="667a8-103">Değişiklikleri geçerli Düzenle ve devam et oturumundan belleğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="667a8-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="667a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="667a8-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="667a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="667a8-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="667a8-106">[out] Meta veri değişim yazma başlanan adresi.</span><span class="sxs-lookup"><span data-stu-id="667a8-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="667a8-107">[in] Değişiklikleri boyutu.</span><span class="sxs-lookup"><span data-stu-id="667a8-107">[in] The size of the changes.</span></span> <span data-ttu-id="667a8-108">Kullanım [Imetadataemit2::getdeltasavesize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) boyutunu belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="667a8-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="667a8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="667a8-109">Requirements</span></span>  
 <span data-ttu-id="667a8-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="667a8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="667a8-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="667a8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="667a8-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="667a8-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="667a8-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="667a8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="667a8-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="667a8-114">See Also</span></span>  
 [<span data-ttu-id="667a8-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="667a8-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="667a8-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="667a8-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)

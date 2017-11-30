---
title: "IMetaDataEmit::Save Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Save
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a2e77ad9ce66a04ef0530dc41f9795c501eed9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="10be5-102">IMetaDataEmit::Save Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10be5-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="10be5-103">Belirtilen adresteki dosya için geçerli kapsamdaki tüm meta verilerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="10be5-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10be5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10be5-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10be5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10be5-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="10be5-106">[in] Kaydetmek için dosya adı.</span><span class="sxs-lookup"><span data-stu-id="10be5-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="10be5-107">Bu değer null ise, bellek içi kopyayı son kullanılan konuma kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="10be5-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="10be5-108">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="10be5-108">[in] Reserved.</span></span> <span data-ttu-id="10be5-109">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="10be5-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10be5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10be5-110">Requirements</span></span>  
 <span data-ttu-id="10be5-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10be5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10be5-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="10be5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10be5-113">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="10be5-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10be5-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10be5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10be5-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10be5-115">See Also</span></span>  
 [<span data-ttu-id="10be5-116">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="10be5-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="10be5-117">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="10be5-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

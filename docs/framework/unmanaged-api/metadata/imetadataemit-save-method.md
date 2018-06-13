---
title: IMetaDataEmit::Save Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6d97d3e4a93985f9b2de3ed9785eff5f7f46c36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444685"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="92035-102">IMetaDataEmit::Save Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92035-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="92035-103">Belirtilen adresteki dosya için geçerli kapsamdaki tüm meta verilerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="92035-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92035-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92035-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92035-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92035-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="92035-106">[in] Kaydetmek için dosya adı.</span><span class="sxs-lookup"><span data-stu-id="92035-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="92035-107">Bu değer null ise, bellek içi kopyayı son kullanılan konuma kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="92035-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="92035-108">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="92035-108">[in] Reserved.</span></span> <span data-ttu-id="92035-109">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92035-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92035-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92035-110">Requirements</span></span>  
 <span data-ttu-id="92035-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92035-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92035-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="92035-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92035-113">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="92035-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92035-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92035-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92035-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92035-115">See Also</span></span>  
 [<span data-ttu-id="92035-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92035-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="92035-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92035-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

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
ms.openlocfilehash: 90ddc540115a60154953ac6e8cb931103a650752
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492422"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="a9b1a-102">IMetaDataEmit::Save Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9b1a-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="a9b1a-103">Belirtilen adresteki bir dosyaya geçerli kapsamdaki tüm meta verileri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a9b1a-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b1a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9b1a-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9b1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9b1a-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="a9b1a-106">[in] Kaydedilecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="a9b1a-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="a9b1a-107">Bu değer null ise, bellek içi kopyayı son kullanılan konuma kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a9b1a-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="a9b1a-108">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="a9b1a-108">[in] Reserved.</span></span> <span data-ttu-id="a9b1a-109">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9b1a-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9b1a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9b1a-110">Requirements</span></span>  
 <span data-ttu-id="a9b1a-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9b1a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9b1a-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a9b1a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9b1a-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="a9b1a-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9b1a-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9b1a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b1a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9b1a-115">See also</span></span>
- [<span data-ttu-id="a9b1a-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9b1a-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a9b1a-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9b1a-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

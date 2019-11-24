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
ms.openlocfilehash: afd60cdf566bea459816ee890d44cc09258de516
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435939"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="ddab8-102">IMetaDataEmit::Save Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ddab8-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="ddab8-103">Saves all metadata in the current scope to the file at the specified address.</span><span class="sxs-lookup"><span data-stu-id="ddab8-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddab8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddab8-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddab8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ddab8-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="ddab8-106">[in] The name of the file to save to.</span><span class="sxs-lookup"><span data-stu-id="ddab8-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="ddab8-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span><span class="sxs-lookup"><span data-stu-id="ddab8-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="ddab8-108">[in] Reserved.</span><span class="sxs-lookup"><span data-stu-id="ddab8-108">[in] Reserved.</span></span> <span data-ttu-id="ddab8-109">Must be zero.</span><span class="sxs-lookup"><span data-stu-id="ddab8-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddab8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddab8-110">Requirements</span></span>  
 <span data-ttu-id="ddab8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddab8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddab8-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ddab8-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ddab8-113">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ddab8-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ddab8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddab8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddab8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddab8-115">See also</span></span>

- [<span data-ttu-id="ddab8-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddab8-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ddab8-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddab8-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

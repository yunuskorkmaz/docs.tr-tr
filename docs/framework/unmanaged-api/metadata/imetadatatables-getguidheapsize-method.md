---
title: IMetaDataTables::GetGuidHeapSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f9a7ddb85865545698809e1865ec571f7c5e9c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674225"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="e5b56-102">IMetaDataTables::GetGuidHeapSize Metodu</span><span class="sxs-lookup"><span data-stu-id="e5b56-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="e5b56-103">GUID yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="e5b56-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5b56-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5b56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5b56-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="e5b56-106">[out] Bayt cinsinden GUID yığın boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5b56-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5b56-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5b56-107">Requirements</span></span>  
 <span data-ttu-id="e5b56-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b56-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5b56-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e5b56-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5b56-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="e5b56-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5b56-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5b56-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b56-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5b56-112">See also</span></span>
- [<span data-ttu-id="e5b56-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5b56-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="e5b56-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5b56-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

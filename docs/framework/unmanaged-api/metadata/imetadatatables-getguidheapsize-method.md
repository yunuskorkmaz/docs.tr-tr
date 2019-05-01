---
title: IMetaDataTables::GetGuidHeapSize Yöntemi
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
ms.openlocfilehash: 812794bc76d475c516effdc950ca6a0b877494c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042425"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="5ef8d-102">IMetaDataTables::GetGuidHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ef8d-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="5ef8d-103">GUID yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5ef8d-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ef8d-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ef8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ef8d-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="5ef8d-106">[out] Bayt cinsinden GUID yığın boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ef8d-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ef8d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ef8d-107">Requirements</span></span>  
 <span data-ttu-id="5ef8d-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ef8d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ef8d-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5ef8d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ef8d-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="5ef8d-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ef8d-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ef8d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ef8d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ef8d-112">See also</span></span>

- [<span data-ttu-id="5ef8d-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ef8d-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="5ef8d-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ef8d-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

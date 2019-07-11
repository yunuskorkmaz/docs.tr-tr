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
ms.openlocfilehash: 0ddbd1c034708326d75c59f8ed4764156f617b81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781493"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="1ac11-102">IMetaDataTables::GetGuidHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ac11-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="1ac11-103">GUID yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="1ac11-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac11-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ac11-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ac11-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ac11-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="1ac11-106">[out] Bayt cinsinden GUID yığın boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ac11-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ac11-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ac11-107">Requirements</span></span>  
 <span data-ttu-id="1ac11-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ac11-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ac11-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1ac11-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1ac11-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1ac11-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1ac11-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ac11-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac11-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ac11-112">See also</span></span>

- [<span data-ttu-id="1ac11-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ac11-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1ac11-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ac11-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

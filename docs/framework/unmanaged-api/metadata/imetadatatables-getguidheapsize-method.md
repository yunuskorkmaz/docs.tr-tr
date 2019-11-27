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
ms.openlocfilehash: cf455b3fb34d8eed78ffaadffad621062c2b9b22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443501"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="f5d58-102">IMetaDataTables::GetGuidHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5d58-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="f5d58-103">GUID yığınının boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="f5d58-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5d58-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5d58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5d58-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="f5d58-106">dışı GUID yığınının bayt cinsinden boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f5d58-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5d58-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5d58-107">Requirements</span></span>  
 <span data-ttu-id="f5d58-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5d58-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5d58-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f5d58-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5d58-110">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f5d58-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5d58-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5d58-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d58-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5d58-112">See also</span></span>

- [<span data-ttu-id="f5d58-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5d58-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="f5d58-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5d58-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

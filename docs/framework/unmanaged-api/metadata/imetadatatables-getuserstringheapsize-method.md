---
title: IMetaDataTables::GetUserStringHeapSize Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: ce8d3356b1f9b73e33ed2d3215c7f8115e64ac70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426642"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="3cb57-102">IMetaDataTables::GetUserStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cb57-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="3cb57-103">Gets the size, in bytes, of the user string heap.</span><span class="sxs-lookup"><span data-stu-id="3cb57-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb57-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cb57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cb57-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cb57-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="3cb57-106">[out] A pointer to the size, in bytes, of the user string heap.</span><span class="sxs-lookup"><span data-stu-id="3cb57-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cb57-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cb57-107">Requirements</span></span>  
 <span data-ttu-id="3cb57-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cb57-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cb57-109">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3cb57-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3cb57-110">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3cb57-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3cb57-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cb57-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb57-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cb57-112">See also</span></span>

- [<span data-ttu-id="3cb57-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cb57-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="3cb57-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cb57-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

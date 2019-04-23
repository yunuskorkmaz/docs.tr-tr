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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d35231e4c36639722635796891056a8902b95940
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097466"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="befc5-102">IMetaDataTables::GetUserStringHeapSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="befc5-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="befc5-103">Kullanıcı dize yığın bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="befc5-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="befc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="befc5-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="befc5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="befc5-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="befc5-106">[out] Bayt cinsinden kullanıcı dize yığın boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="befc5-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="befc5-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="befc5-107">Requirements</span></span>  
 <span data-ttu-id="befc5-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="befc5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="befc5-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="befc5-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="befc5-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="befc5-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="befc5-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="befc5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="befc5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="befc5-112">See also</span></span>

- [<span data-ttu-id="befc5-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="befc5-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="befc5-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="befc5-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

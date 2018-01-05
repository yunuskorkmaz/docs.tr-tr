---
title: IMetaDataTables::GetUserStringHeapSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetUserStringHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b1f4f1b8c3cafb28c2b84867dbe5ac3f8424e8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="4b8fd-102">IMetaDataTables::GetUserStringHeapSize Metodu</span><span class="sxs-lookup"><span data-stu-id="4b8fd-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="4b8fd-103">Kullanıcı dize yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="4b8fd-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b8fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b8fd-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b8fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b8fd-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="4b8fd-106">[out] Bir işaretçi kullanıcı dize yığın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="4b8fd-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b8fd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b8fd-107">Requirements</span></span>  
 <span data-ttu-id="4b8fd-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b8fd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b8fd-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b8fd-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b8fd-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4b8fd-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b8fd-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b8fd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8fd-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b8fd-112">See Also</span></span>  
 [<span data-ttu-id="4b8fd-113">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b8fd-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="4b8fd-114">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b8fd-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

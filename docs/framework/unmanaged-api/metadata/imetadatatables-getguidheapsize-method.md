---
title: IMetaDataTables::GetGuidHeapSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetGuidHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76a2aa4495a9f34a57c8a84ec40ab946abc64532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="317a1-102">IMetaDataTables::GetGuidHeapSize Metodu</span><span class="sxs-lookup"><span data-stu-id="317a1-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="317a1-103">GUID yığın bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="317a1-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="317a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="317a1-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="317a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="317a1-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="317a1-106">[out] Bir işaretçi GUID yığın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="317a1-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="317a1-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="317a1-107">Requirements</span></span>  
 <span data-ttu-id="317a1-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="317a1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="317a1-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="317a1-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="317a1-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="317a1-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="317a1-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="317a1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="317a1-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="317a1-112">See Also</span></span>  
 [<span data-ttu-id="317a1-113">Imetadatatables arabirimi</span><span class="sxs-lookup"><span data-stu-id="317a1-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="317a1-114">Imetadatatables2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="317a1-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

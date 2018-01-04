---
title: "IMetaDataEmit::SaveToStream Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SaveToStream
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 135faea41ab1a8165e315b8d0815abc48ba7fd38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="25c2a-102">IMetaDataEmit::SaveToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25c2a-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="25c2a-103">Belirtilen geçerli kapsamdaki tüm meta veriler kaydeder `IStream`.</span><span class="sxs-lookup"><span data-stu-id="25c2a-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25c2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25c2a-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25c2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25c2a-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="25c2a-106">[in] Kaydetmek için yazılabilir akış.</span><span class="sxs-lookup"><span data-stu-id="25c2a-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="25c2a-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="25c2a-107">[in] Reserved.</span></span> <span data-ttu-id="25c2a-108">Sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25c2a-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25c2a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25c2a-109">Requirements</span></span>  
 <span data-ttu-id="25c2a-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25c2a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25c2a-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25c2a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25c2a-112">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="25c2a-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25c2a-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25c2a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c2a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25c2a-114">See Also</span></span>  
 [<span data-ttu-id="25c2a-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25c2a-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="25c2a-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25c2a-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

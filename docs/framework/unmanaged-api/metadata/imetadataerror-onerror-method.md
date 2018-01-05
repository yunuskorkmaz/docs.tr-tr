---
title: "IMetaDataError::OnError Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataError.OnError
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6e136f3fd76b9eb2be1e49a48316dc65c481fc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="f2447-102">IMetaDataError::OnError Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2447-102">IMetaDataError::OnError Method</span></span>
<span data-ttu-id="f2447-103">Meta veri birleştirme sırasında oluşan hataları bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2447-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2447-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2447-104">Syntax</span></span>  
  
```  
HRESULT OnError (  
    [in] HRESULT   hrError,   
    [in] mdToken   token  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2447-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2447-105">Parameters</span></span>  
 `hrError`  
 <span data-ttu-id="f2447-106">[in] Çağıran yönteme döndürülen HRESULT hata değeri.</span><span class="sxs-lookup"><span data-stu-id="f2447-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="f2447-107">[in] Hata oluştuğunda, birleştirilen kod nesnesinin meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="f2447-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2447-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2447-108">Requirements</span></span>  
 <span data-ttu-id="f2447-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2447-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2447-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f2447-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f2447-111">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f2447-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2447-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2447-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2447-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2447-113">See Also</span></span>  
 [<span data-ttu-id="f2447-114">IMetaDataError Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2447-114">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)

---
title: IGCHost::Collect Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdacb454783cfb8f90ea5a73807f0a199e16475d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154784"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="3655f-102">IGCHost::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3655f-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="3655f-103">Geçerli çöp toplama durumundan bağımsız olarak verilen oluşturma için gerçekleşmesi için bir koleksiyon zorlar.</span><span class="sxs-lookup"><span data-stu-id="3655f-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3655f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3655f-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3655f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3655f-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="3655f-106">[in] Çöp toplama gerçekleştirileceği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="3655f-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="3655f-107">Tüm nesiller çöp toplama yapılacaktır -1 değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="3655f-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3655f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3655f-108">Requirements</span></span>  
 <span data-ttu-id="3655f-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3655f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3655f-110">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="3655f-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="3655f-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3655f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3655f-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3655f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3655f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3655f-113">See also</span></span>

- [<span data-ttu-id="3655f-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3655f-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)

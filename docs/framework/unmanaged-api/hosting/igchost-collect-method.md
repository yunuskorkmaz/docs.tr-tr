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
ms.openlocfilehash: bce005a677dcb74c176a6dddfb2726f6b1fd0e8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436913"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="c5d1e-102">IGCHost::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5d1e-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="c5d1e-103">Geçerli çöp toplama durumu bağımsız olarak verilen oluşturma için gerçekleşmesi için bir koleksiyon zorlar.</span><span class="sxs-lookup"><span data-stu-id="c5d1e-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5d1e-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5d1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5d1e-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="c5d1e-106">[in] Çöp toplama gerçekleştirileceği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c5d1e-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="c5d1e-107">-1 değeri, tüm nesli çöp toplama yapılacaktır gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5d1e-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5d1e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5d1e-108">Requirements</span></span>  
 <span data-ttu-id="c5d1e-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5d1e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5d1e-110">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="c5d1e-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c5d1e-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c5d1e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5d1e-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5d1e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d1e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5d1e-113">See Also</span></span>  
 [<span data-ttu-id="c5d1e-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5d1e-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)

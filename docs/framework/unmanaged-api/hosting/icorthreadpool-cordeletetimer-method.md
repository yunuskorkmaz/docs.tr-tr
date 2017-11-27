---
title: "ICorThreadpool::CorDeleteTimer Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorDeleteTimer
api_location: mscoree.dll
api_type: COM
f1_keywords: CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d72c260d4839e38ca02f4e95c6ea41f493b3dda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="335ea-102">ICorThreadpool::CorDeleteTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="335ea-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="335ea-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="335ea-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="335ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="335ea-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="335ea-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="335ea-105">Requirements</span></span>  
 <span data-ttu-id="335ea-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="335ea-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="335ea-107">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="335ea-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="335ea-108">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="335ea-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="335ea-109">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="335ea-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="335ea-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="335ea-110">See Also</span></span>  
 [<span data-ttu-id="335ea-111">Icorthreadpool arabirimi</span><span class="sxs-lookup"><span data-stu-id="335ea-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)

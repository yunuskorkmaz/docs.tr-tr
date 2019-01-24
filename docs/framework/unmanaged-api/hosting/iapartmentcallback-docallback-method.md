---
title: IApartmentCallback::DoCallback Yöntemi
ms.date: 03/30/2017
api_name:
- IApartmentCallback.DoCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- DoCallback
helpviewer_keywords:
- IApartmentCallback::DoCallback method [.NET Framework hosting]
- DoCallback method [.NET Framework hosting]
ms.assetid: 8edad30c-30ff-4bee-813c-75525a82fc93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f64d554ee0bcd93d30dd617177c4e1e33e57aa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648877"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="48075-102">IApartmentCallback::DoCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48075-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="48075-103">Bir grup içinde belirtilen işlevi yürütür.</span><span class="sxs-lookup"><span data-stu-id="48075-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48075-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48075-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48075-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48075-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="48075-106">[in] Grup içinde yürütülecek işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="48075-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="48075-107">[in] İşlevin bağımsız değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="48075-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48075-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48075-108">Requirements</span></span>  
 <span data-ttu-id="48075-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48075-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48075-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48075-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48075-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="48075-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48075-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48075-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48075-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48075-113">See also</span></span>
- [<span data-ttu-id="48075-114">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48075-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)

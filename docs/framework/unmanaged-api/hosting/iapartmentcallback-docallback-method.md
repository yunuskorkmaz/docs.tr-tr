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
ms.openlocfilehash: ba1dc2a1ec8b0b3b5ec25036cab6362237efe98f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430762"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="dbce7-102">IApartmentCallback::DoCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dbce7-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="dbce7-103">Belirtilen işlev bir grup içinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="dbce7-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbce7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbce7-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbce7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dbce7-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="dbce7-106">[in] İçinde grup yürütülecek işlevi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dbce7-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="dbce7-107">[in] İşlevin bağımsız değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dbce7-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbce7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbce7-108">Requirements</span></span>  
 <span data-ttu-id="dbce7-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbce7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbce7-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbce7-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbce7-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dbce7-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbce7-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbce7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbce7-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbce7-113">See Also</span></span>  
 [<span data-ttu-id="dbce7-114">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbce7-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)

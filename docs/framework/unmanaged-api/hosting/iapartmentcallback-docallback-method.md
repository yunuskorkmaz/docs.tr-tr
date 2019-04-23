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
ms.openlocfilehash: 77a2ccaf6f972fadd8396378dc7777ec4c85120d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110233"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="02f52-102">IApartmentCallback::DoCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02f52-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="02f52-103">Bir grup içinde belirtilen işlevi yürütür.</span><span class="sxs-lookup"><span data-stu-id="02f52-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f52-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02f52-104">Syntax</span></span>  
  
```  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02f52-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02f52-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="02f52-106">[in] Grup içinde yürütülecek işlev işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="02f52-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="02f52-107">[in] İşlevin bağımsız değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="02f52-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f52-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02f52-108">Requirements</span></span>  
 <span data-ttu-id="02f52-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02f52-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02f52-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02f52-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02f52-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="02f52-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02f52-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02f52-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f52-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02f52-113">See also</span></span>

- [<span data-ttu-id="02f52-114">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02f52-114">IApartmentCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)

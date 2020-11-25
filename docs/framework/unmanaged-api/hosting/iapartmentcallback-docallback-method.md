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
ms.openlocfilehash: e3031bf123ff9107b4cebc0723f1be0d423bdaec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721757"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="1e558-102">IApartmentCallback::DoCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e558-102">IApartmentCallback::DoCallback Method</span></span>

<span data-ttu-id="1e558-103">Belirtilen işlevi bir apartman içinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="1e558-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e558-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1e558-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e558-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e558-105">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="1e558-106">'ndaki Apartman içinde yürütülecek işleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e558-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="1e558-107">'ndaki İşlevin bağımsız değişkenine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e558-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e558-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e558-108">Requirements</span></span>  

 <span data-ttu-id="1e558-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e558-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e558-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1e558-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e558-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1e558-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e558-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e558-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e558-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e558-113">See also</span></span>

- [<span data-ttu-id="1e558-114">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e558-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)

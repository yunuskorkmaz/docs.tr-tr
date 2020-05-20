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
ms.openlocfilehash: 1a56c3ebe4b1c528f9c6555bdfbf1270a438410d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617119"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="7c25e-102">IApartmentCallback::DoCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c25e-102">IApartmentCallback::DoCallback Method</span></span>
<span data-ttu-id="7c25e-103">Belirtilen işlevi bir apartman içinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="7c25e-103">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c25e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7c25e-104">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c25e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c25e-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="7c25e-106">'ndaki Apartman içinde yürütülecek işleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c25e-106">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="7c25e-107">'ndaki İşlevin bağımsız değişkenine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c25e-107">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c25e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c25e-108">Requirements</span></span>  
 <span data-ttu-id="7c25e-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c25e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c25e-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c25e-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c25e-111">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7c25e-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c25e-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c25e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c25e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c25e-113">See also</span></span>

- [<span data-ttu-id="7c25e-114">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c25e-114">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)

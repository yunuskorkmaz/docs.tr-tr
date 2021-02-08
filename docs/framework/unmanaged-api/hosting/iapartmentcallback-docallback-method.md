---
description: 'Şu konuda daha fazla bilgi edinin: IApartmentCallback::D oCallback yöntemi'
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
ms.openlocfilehash: 65b7f496f953f08e099bf13ef8212c7d6e1026ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785116"
---
# <a name="iapartmentcallbackdocallback-method"></a><span data-ttu-id="7c75b-103">IApartmentCallback::DoCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c75b-103">IApartmentCallback::DoCallback Method</span></span>

<span data-ttu-id="7c75b-104">Belirtilen işlevi bir apartman içinde yürütür.</span><span class="sxs-lookup"><span data-stu-id="7c75b-104">Executes the specified function within an apartment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c75b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c75b-105">Syntax</span></span>  
  
```cpp  
HRESULT _stdcall DoCallback(  
    [in] SIZE_T pFunc,  
    [in] SIZE_T pData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c75b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c75b-106">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="7c75b-107">'ndaki Apartman içinde yürütülecek işleve yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c75b-107">[in] A pointer to the function to be executed within the apartment.</span></span>  
  
 `pData`  
 <span data-ttu-id="7c75b-108">'ndaki İşlevin bağımsız değişkenine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c75b-108">[in] A pointer to the function's argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c75b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c75b-109">Requirements</span></span>  

 <span data-ttu-id="7c75b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c75b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c75b-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7c75b-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c75b-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7c75b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c75b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c75b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c75b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c75b-114">See also</span></span>

- [<span data-ttu-id="7c75b-115">IApartmentCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c75b-115">IApartmentCallback Interface</span></span>](iapartmentcallback-interface.md)

---
title: WAITORTIMERCALLBACK İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8cf12fc6828c5e439a6a86532f22b8a598a9f03
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120997"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="cc0bb-102">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="cc0bb-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="cc0bb-103">Bekleme işleyen ana bildiren bir işleve işaret eder (<xref:System.Threading.WaitHandle>) sinyal veya zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cc0bb-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="cc0bb-104">Bu işlev işaretçisi içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc0bb-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc0bb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc0bb-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc0bb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc0bb-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="cc0bb-107">[in] Ana bilgisayar tarafından tanımlanan bilgileri içeren bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc0bb-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="cc0bb-108">[in] `true` bekleme tanıtıcısı zaman aşımına uğradı, varsa veya `false` , sinyal değilse.</span><span class="sxs-lookup"><span data-stu-id="cc0bb-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc0bb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cc0bb-109">Remarks</span></span>  
 <span data-ttu-id="cc0bb-110">İşleve `WAITORTIMERCALLBACK` noktaları bir geri çağırma işlevidir ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cc0bb-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc0bb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc0bb-111">Requirements</span></span>  
 <span data-ttu-id="cc0bb-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc0bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc0bb-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cc0bb-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc0bb-114">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="cc0bb-114">**Library:** MSCorWks.dll</span></span>  
  
 **<span data-ttu-id="cc0bb-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="cc0bb-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cc0bb-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc0bb-116">See also</span></span>

- [<span data-ttu-id="cc0bb-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cc0bb-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

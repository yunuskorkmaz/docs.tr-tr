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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120997"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="fafda-102">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="fafda-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="fafda-103">Bekleme işleyen ana bildiren bir işleve işaret eder (<xref:System.Threading.WaitHandle>) sinyal veya zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fafda-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="fafda-104">Bu işlev işaretçisi içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fafda-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fafda-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fafda-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fafda-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fafda-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="fafda-107">[in] Ana bilgisayar tarafından tanımlanan bilgileri içeren bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fafda-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="fafda-108">[in] `true` bekleme tanıtıcısı zaman aşımına uğradı, varsa veya `false` , sinyal değilse.</span><span class="sxs-lookup"><span data-stu-id="fafda-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fafda-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fafda-109">Remarks</span></span>  
 <span data-ttu-id="fafda-110">İşleve `WAITORTIMERCALLBACK` noktaları bir geri çağırma işlevidir ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fafda-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fafda-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fafda-111">Requirements</span></span>  
 <span data-ttu-id="fafda-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fafda-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fafda-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fafda-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fafda-114">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="fafda-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="fafda-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fafda-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fafda-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fafda-116">See also</span></span>

- [<span data-ttu-id="fafda-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fafda-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

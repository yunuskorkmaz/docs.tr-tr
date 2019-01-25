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
ms.openlocfilehash: 1d36ae3ef63c1324f77786ad55674bbdc257d984
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607140"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="d4d5f-102">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="d4d5f-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="d4d5f-103">Bekleme işleyen ana bildiren bir işleve işaret eder (<xref:System.Threading.WaitHandle>) sinyal veya zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d4d5f-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="d4d5f-104">Bu işlev işaretçisi içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d4d5f-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d5f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4d5f-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4d5f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4d5f-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="d4d5f-107">[in] Ana bilgisayar tarafından tanımlanan bilgileri içeren bir nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d4d5f-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="d4d5f-108">[in] `true` bekleme tanıtıcısı zaman aşımına uğradı, varsa veya `false` , sinyal değilse.</span><span class="sxs-lookup"><span data-stu-id="d4d5f-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4d5f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4d5f-109">Remarks</span></span>  
 <span data-ttu-id="d4d5f-110">İşleve `WAITORTIMERCALLBACK` noktaları bir geri çağırma işlevidir ve uygulamanın barındırma yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d4d5f-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d5f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4d5f-111">Requirements</span></span>  
 <span data-ttu-id="d4d5f-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4d5f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d5f-113">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4d5f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4d5f-114">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="d4d5f-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d4d5f-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d5f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d5f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4d5f-116">See also</span></span>
- [<span data-ttu-id="d4d5f-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d4d5f-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

---
description: ': ICLROnEventManager arabirimi hakkında daha fazla bilgi edinin'
title: ICLROnEventManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: 7a9c0beec5083bc93f5361bb0e701da5beeedea2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789833"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="fc1ed-103">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc1ed-103">ICLROnEventManager Interface</span></span>

<span data-ttu-id="fc1ed-104">Ana bilgisayarın ortak dil çalışma zamanı (CLR) olayları için geri çağırmaları kaydetmesine ve kaydını kaydetmesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc1ed-104">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc1ed-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fc1ed-105">Methods</span></span>  
  
|<span data-ttu-id="fc1ed-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fc1ed-106">Method</span></span>|<span data-ttu-id="fc1ed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc1ed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc1ed-108">RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc1ed-108">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="fc1ed-109">Belirtilen olay için bir geri çağırma işaretçisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fc1ed-109">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="fc1ed-110">UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc1ed-110">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="fc1ed-111">Belirtilen olay için önceden kaydedilmiş bir geri çağırma işaretçisinin kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="fc1ed-111">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc1ed-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc1ed-112">Remarks</span></span>  

 <span data-ttu-id="fc1ed-113">Olay geri çağırmaları kaydetmek ve kaydını silmek için, ana bilgisayar `ICLROnEventManager` [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) metodunu çağırarak öğesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="fc1ed-113">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc1ed-114">[EClrEvent](eclrevent-enumeration.md) tarafından tanımlanan olaylar birden çok kez tetiklenebilir ve farklı iş PARÇACıKLARıNDAN clr 'nin kaldırılmasına veya devre dışı bırakılmasına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="fc1ed-114">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc1ed-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc1ed-115">Requirements</span></span>  

 <span data-ttu-id="fc1ed-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc1ed-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc1ed-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc1ed-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc1ed-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fc1ed-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc1ed-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc1ed-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc1ed-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc1ed-120">See also</span></span>

- [<span data-ttu-id="fc1ed-121">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fc1ed-121">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="fc1ed-122">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc1ed-122">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="fc1ed-123">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc1ed-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="fc1ed-124">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fc1ed-124">Hosting Interfaces</span></span>](hosting-interfaces.md)

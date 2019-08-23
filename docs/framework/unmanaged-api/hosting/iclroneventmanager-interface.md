---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3633db69877db771d919c9f43da4809f8321f77c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951194"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="33b3a-102">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33b3a-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="33b3a-103">Ana bilgisayarın ortak dil çalışma zamanı (CLR) olayları için geri çağırmaları kaydetmesine ve kaydını kaydetmesine izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="33b3a-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33b3a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="33b3a-104">Methods</span></span>  
  
|<span data-ttu-id="33b3a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="33b3a-105">Method</span></span>|<span data-ttu-id="33b3a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33b3a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33b3a-107">RegisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33b3a-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="33b3a-108">Belirtilen olay için bir geri çağırma işaretçisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="33b3a-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="33b3a-109">UnregisterActionOnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33b3a-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="33b3a-110">Belirtilen olay için önceden kaydedilmiş bir geri çağırma işaretçisinin kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="33b3a-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33b3a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33b3a-111">Remarks</span></span>  
 <span data-ttu-id="33b3a-112">Olay geri çağırmaları kaydetmek ve kaydını silmek için, ana bilgisayar `ICLROnEventManager` [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodunu çağırarak öğesine bir başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="33b3a-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33b3a-113">[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) tarafından tanımlanan olaylar birden çok kez tetiklenebilir ve farklı iş PARÇACıKLARıNDAN clr 'nin kaldırılmasına veya devre dışı bırakılmasına işaret edebilir.</span><span class="sxs-lookup"><span data-stu-id="33b3a-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33b3a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33b3a-114">Requirements</span></span>  
 <span data-ttu-id="33b3a-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33b3a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33b3a-116">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="33b3a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33b3a-117">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="33b3a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33b3a-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33b3a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b3a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33b3a-119">See also</span></span>

- [<span data-ttu-id="33b3a-120">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="33b3a-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="33b3a-121">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33b3a-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="33b3a-122">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33b3a-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="33b3a-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="33b3a-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

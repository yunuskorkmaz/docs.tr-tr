---
title: IActionOnCLREvent Arabirimi
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 4e72cd8bee2cb4f35155d7b99cfe8d9cf63f463a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616079"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="e34c2-102">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e34c2-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="e34c2-103">[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) metoduna yapılan bir çağrı kullanılarak kaydedilmiş olaylarda geri çağırmaları gerçekleştiren [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e34c2-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e34c2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e34c2-104">Methods</span></span>  
  
|<span data-ttu-id="e34c2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e34c2-105">Method</span></span>|<span data-ttu-id="e34c2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e34c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e34c2-107">OnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e34c2-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="e34c2-108">Kayıtlı bir olay için geri arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e34c2-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e34c2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e34c2-109">Requirements</span></span>  
 <span data-ttu-id="e34c2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e34c2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e34c2-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e34c2-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e34c2-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e34c2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e34c2-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e34c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e34c2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e34c2-114">See also</span></span>

- [<span data-ttu-id="e34c2-115">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e34c2-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="e34c2-116">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e34c2-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e34c2-117">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e34c2-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="e34c2-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e34c2-118">Hosting Interfaces</span></span>](hosting-interfaces.md)

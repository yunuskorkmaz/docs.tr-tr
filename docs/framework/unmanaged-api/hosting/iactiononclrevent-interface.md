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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 864a8a4dd9f96da2fd0e0025848a910b4f8b0a70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180528"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="cd78f-102">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd78f-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="cd78f-103">Sağlar [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) bir çağrı kullanılarak kaydedilmiş olayları geri çağırmaları gerçekleştiren yöntemi [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cd78f-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd78f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cd78f-104">Methods</span></span>  
  
|<span data-ttu-id="cd78f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cd78f-105">Method</span></span>|<span data-ttu-id="cd78f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd78f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd78f-107">OnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd78f-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="cd78f-108">Kayıtlı bir olay için bir geri arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="cd78f-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd78f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd78f-109">Requirements</span></span>  
 <span data-ttu-id="cd78f-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd78f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd78f-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd78f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd78f-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cd78f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd78f-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd78f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd78f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd78f-114">See also</span></span>

- [<span data-ttu-id="cd78f-115">EClrEvent Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="cd78f-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="cd78f-116">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd78f-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="cd78f-117">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd78f-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="cd78f-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cd78f-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

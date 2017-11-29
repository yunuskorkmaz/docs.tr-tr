---
title: IActionOnCLREvent Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent
helpviewer_keywords: IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eecc04fea993de3c502d1a203f0023c81c3b7909
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="15a3b-102">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15a3b-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="15a3b-103">Sağlar [Iactiononclrevent::ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) geri aramalar için bir çağrı kullanılarak kaydedilmiş olayları gerçekleştirir yöntemi [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="15a3b-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15a3b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="15a3b-104">Methods</span></span>  
  
|<span data-ttu-id="15a3b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="15a3b-105">Method</span></span>|<span data-ttu-id="15a3b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15a3b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15a3b-107">OnEvent yöntemi</span><span class="sxs-lookup"><span data-stu-id="15a3b-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="15a3b-108">Kayıtlı bir olay için bir geri çağırma gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="15a3b-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15a3b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15a3b-109">Requirements</span></span>  
 <span data-ttu-id="15a3b-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a3b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15a3b-111">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15a3b-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15a3b-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="15a3b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15a3b-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15a3b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15a3b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15a3b-114">See Also</span></span>  
 [<span data-ttu-id="15a3b-115">EClrEvent numaralandırması</span><span class="sxs-lookup"><span data-stu-id="15a3b-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="15a3b-116">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="15a3b-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="15a3b-117">Iclroneventmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="15a3b-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="15a3b-118">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15a3b-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

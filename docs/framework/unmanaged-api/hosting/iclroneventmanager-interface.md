---
title: ICLROnEventManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager
helpviewer_keywords: ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3f792af3e01d476768961928272cb6166a144f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="fafca-102">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fafca-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="fafca-103">Kaydolun ve ortak dil çalışma zamanı (CLR) olayları için geri çağırmaları kaydı için ana izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="fafca-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fafca-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fafca-104">Methods</span></span>  
  
|<span data-ttu-id="fafca-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fafca-105">Method</span></span>|<span data-ttu-id="fafca-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fafca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fafca-107">RegisterActionOnEvent yöntemi</span><span class="sxs-lookup"><span data-stu-id="fafca-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="fafca-108">Belirtilen olay için bir geri çağırma işaretçi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fafca-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="fafca-109">UnregisterActionOnEvent yöntemi</span><span class="sxs-lookup"><span data-stu-id="fafca-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="fafca-110">Belirtilen olay için daha önce kaydedilmiş geri işaretçi kaydını siler.</span><span class="sxs-lookup"><span data-stu-id="fafca-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fafca-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fafca-111">Remarks</span></span>  
 <span data-ttu-id="fafca-112">Konak kaydetmek ve olay geri aramalar kaydı için bir başvuru edinir `ICLROnEventManager` çağırarak [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fafca-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fafca-113">Tarafından tanımlanan olayları [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) birden çok kez ve bir kaldırma veya CLR devre dışı bırakma sinyal için farklı iş parçacıklarından tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="fafca-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fafca-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fafca-114">Requirements</span></span>  
 <span data-ttu-id="fafca-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fafca-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fafca-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fafca-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fafca-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fafca-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fafca-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fafca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fafca-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fafca-119">See Also</span></span>  
 [<span data-ttu-id="fafca-120">EClrEvent numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fafca-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="fafca-121">Iactiononclrevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="fafca-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="fafca-122">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="fafca-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="fafca-123">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fafca-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

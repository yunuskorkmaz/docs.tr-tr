---
description: 'Daha fazla bilgi edinin: IActionOnCLREvent arabirimi'
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
ms.openlocfilehash: 9d762635247f897663f4c6f2badf67edf98bd5d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785178"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="27ac2-103">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27ac2-103">IActionOnCLREvent Interface</span></span>

<span data-ttu-id="27ac2-104">[ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) metoduna yapılan bir çağrı kullanılarak kaydedilmiş olaylarda geri çağırmaları gerçekleştiren [IActionOnCLREvent:: OnEvent](iactiononclrevent-onevent-method.md) metodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="27ac2-104">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27ac2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="27ac2-105">Methods</span></span>  
  
|<span data-ttu-id="27ac2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="27ac2-106">Method</span></span>|<span data-ttu-id="27ac2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27ac2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27ac2-108">OnEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27ac2-108">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="27ac2-109">Kayıtlı bir olay için geri arama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="27ac2-109">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27ac2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27ac2-110">Requirements</span></span>  

 <span data-ttu-id="27ac2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27ac2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27ac2-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="27ac2-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27ac2-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="27ac2-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27ac2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27ac2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ac2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27ac2-115">See also</span></span>

- [<span data-ttu-id="27ac2-116">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="27ac2-116">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="27ac2-117">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27ac2-117">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="27ac2-118">ICLROnEventManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27ac2-118">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="27ac2-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="27ac2-119">Hosting Interfaces</span></span>](hosting-interfaces.md)

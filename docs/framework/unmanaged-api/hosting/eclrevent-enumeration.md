---
title: "EClrEvent Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d453cf7d3c7613397890c2d49a2dbe81a2e5d81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="4d687-102">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4d687-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="4d687-103">Ana bilgisayar geri aramalar kaydedebilirsiniz ortak dil çalışma zamanı (CLR) olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4d687-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d687-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d687-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="4d687-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4d687-105">Members</span></span>  
  
|<span data-ttu-id="4d687-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4d687-106">Member</span></span>|<span data-ttu-id="4d687-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d687-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="4d687-108">Önemli bir CLR hata belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d687-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="4d687-109">Belirli bir eklentiyi belirtir <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="4d687-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="4d687-110">Yönetilen hata ayıklama Yardımcısı (MDA) ileti oluşturulan belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d687-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="4d687-111">Bir yığın taşması hata oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4d687-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d687-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d687-112">Remarks</span></span>  
 <span data-ttu-id="4d687-113">Ana bilgisayar tarafından açıklanan olay türlerinden herhangi birini için geri çağırmaları kaydedebilirsiniz `EClrEvent` yöntemlerini çağırarak [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4d687-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="4d687-114">Konak bir işaretçi çağırarak bu arabirime alır [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4d687-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="4d687-115">`Event_CLRDisabled` Ve `Event_DomainUnload` olayları yükseltilmiş birden çok kez ve bir kaldırma veya CLR devre dışı bırakma sinyal için farklı iş parçacıklarından.</span><span class="sxs-lookup"><span data-stu-id="4d687-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="4d687-116">`Event_MDAFired` Olayını oluşturulmasını bir [Mdaınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) MDA ileti ayrıntılarını içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="4d687-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="4d687-117">Mda'lar hakkında daha fazla bilgi için bkz: [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="4d687-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d687-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d687-118">Requirements</span></span>  
 <span data-ttu-id="4d687-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d687-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d687-120">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4d687-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d687-121">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d687-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d687-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d687-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d687-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d687-123">See Also</span></span>  
 [<span data-ttu-id="4d687-124">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d687-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="4d687-125">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d687-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="4d687-126">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4d687-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

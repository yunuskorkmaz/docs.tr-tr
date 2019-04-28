---
title: EClrEvent Numaralandırması
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13d564be68d6b49a1616be97710312f33f828d48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628665"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="9ef31-102">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9ef31-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="9ef31-103">Konak geri çağırmaları kaydedebilirsiniz ortak dil çalışma zamanı (CLR) olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ef31-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef31-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ef31-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="9ef31-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9ef31-105">Members</span></span>  
  
|<span data-ttu-id="9ef31-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9ef31-106">Member</span></span>|<span data-ttu-id="9ef31-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ef31-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="9ef31-108">Önemli bir CLR hata belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ef31-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="9ef31-109">Belirli bir eklentiyi belirtir <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9ef31-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="9ef31-110">Yönetilen hata ayıklama Yardımcısı (MDA) iletisini oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ef31-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="9ef31-111">Bir yığın taşması hata oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ef31-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ef31-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ef31-112">Remarks</span></span>  
 <span data-ttu-id="9ef31-113">Ana bilgisayar tarafından açıklanan olay türlerinden herhangi birini geri kaydedebilirsiniz `EClrEvent` yöntemleri çağırarak [Iclroneventmanager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9ef31-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="9ef31-114">Konak, çağırarak bu arabirim için bir işaretçi alır [Iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9ef31-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="9ef31-115">`Event_CLRDisabled` Ve `Event_DomainUnload` birden çok kez ve bir kaldırma veya CLR devre dışı bırakma sinyal farklı iş parçacıklarından olayları'nin yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="9ef31-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="9ef31-116">`Event_MDAFired` Olayını oluşturulmasını bir [Mdaınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) MDA ileti ayrıntılarını içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="9ef31-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="9ef31-117">Mda'leri hakkında daha fazla bilgi için bkz: [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="9ef31-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ef31-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ef31-118">Requirements</span></span>  
 <span data-ttu-id="9ef31-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ef31-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef31-120">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ef31-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ef31-121">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ef31-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ef31-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef31-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef31-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ef31-123">See also</span></span>

- [<span data-ttu-id="9ef31-124">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ef31-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="9ef31-125">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ef31-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9ef31-126">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9ef31-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

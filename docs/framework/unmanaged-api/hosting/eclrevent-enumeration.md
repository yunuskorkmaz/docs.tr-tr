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
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131128"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="f7d35-102">EClrEvent Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f7d35-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="f7d35-103">Konağın geri çağırmaları kaydedebileceği ortak dil çalışma zamanı (CLR) olaylarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f7d35-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7d35-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="f7d35-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f7d35-105">Members</span></span>  
  
|<span data-ttu-id="f7d35-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f7d35-106">Member</span></span>|<span data-ttu-id="f7d35-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7d35-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="f7d35-108">Önemli bir CLR hatası belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7d35-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="f7d35-109">Belirli bir <xref:System.AppDomain>kaldırılmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7d35-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="f7d35-110">Yönetilen hata ayıklama Yardımcısı (MDA) iletisinin oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7d35-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="f7d35-111">Yığın taşması hatası oluştuğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7d35-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7d35-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7d35-112">Remarks</span></span>  
 <span data-ttu-id="f7d35-113">Ana bilgisayar, [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) arabiriminin yöntemlerini çağırarak `EClrEvent` tarafından tanımlanan olay türlerinden herhangi biri için geri çağırmaları kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="f7d35-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="f7d35-114">Ana bilgisayar [ICLRControl:: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metodunu çağırarak bu arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="f7d35-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="f7d35-115">`Event_CLRDisabled` ve `Event_DomainUnload` olayları birden çok kez ve farklı iş parçacıklarından, CLR 'nin bir yüklemesini veya devre dışı bırakılmasını bildirmek için bir kereden fazla oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="f7d35-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="f7d35-116">`Event_MDAFired` olay, MDA iletisinin ayrıntılarını içeren bir [Mdadınfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) örneği oluşturulmasını başlatır.</span><span class="sxs-lookup"><span data-stu-id="f7d35-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="f7d35-117">MDAs hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="f7d35-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d35-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7d35-118">Requirements</span></span>  
 <span data-ttu-id="f7d35-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7d35-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d35-120">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f7d35-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7d35-121">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f7d35-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7d35-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7d35-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d35-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7d35-123">See also</span></span>

- [<span data-ttu-id="f7d35-124">IActionOnCLREvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7d35-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="f7d35-125">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7d35-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f7d35-126">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f7d35-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

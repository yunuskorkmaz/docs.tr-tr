---
title: MDAInfo Yapısı
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5164e85ecc97de99dcc493c2ba5efa8fc3468471
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443186"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="39838-102">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="39838-102">MDAInfo Structure</span></span>
<span data-ttu-id="39838-103">Hakkında ayrıntılar sağlar `Event_MDAFired` yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikleyen olayı.</span><span class="sxs-lookup"><span data-stu-id="39838-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39838-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39838-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="39838-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="39838-105">Members</span></span>  
  
|<span data-ttu-id="39838-106">Üye</span><span class="sxs-lookup"><span data-stu-id="39838-106">Member</span></span>|<span data-ttu-id="39838-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="39838-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="39838-108">Geçerli MDA başlığı.</span><span class="sxs-lookup"><span data-stu-id="39838-108">The title of the current MDA.</span></span> <span data-ttu-id="39838-109">Başlık tetiklenen hatası türünü açıklar `Event_MDAFired` olay.</span><span class="sxs-lookup"><span data-stu-id="39838-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="39838-110">Geçerli mda'sı tarafından sağlanan çıkış ileti.</span><span class="sxs-lookup"><span data-stu-id="39838-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39838-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39838-111">Remarks</span></span>  
 <span data-ttu-id="39838-112">Yönetilen hata ayıklama Yardımcıları (Mda'lar) çalışma zamanı yürütme altyapısı ortak dil çalışma zamanı (CLR) geçersiz koşulları tanımlama gibi görevleri gerçekleştirmek için birlikte çalışmak yardımları hata ayıklama veya durumuyla ilgili ek bilgi döküm alma altyapısı.</span><span class="sxs-lookup"><span data-stu-id="39838-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="39838-113">Mda'lar, aksi takdirde tuzak zor olan olaylar hakkında XML iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39838-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="39838-114">Bunlar yönetilen ve yönetilmeyen kodu arasında geçişler hata ayıklama için özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="39838-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="39838-115">Bir MDA oluşturulmasını tetikleyen bir olay başlatıldığında çalışma zamanı aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="39838-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="39838-116">Konak değil kaydedildiyse bir [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) çağırarak örneği [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) , bildirim almak için bir `Event_MDAFired` olay, çalışma zamanı geçer ile kendi Varsayılan, barındırılan dışı davranış.</span><span class="sxs-lookup"><span data-stu-id="39838-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="39838-117">Bu olay işleyicisi konağı kaydedildiyse, çalışma zamanı işleme bir hata ayıklayıcısı ekli olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="39838-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="39838-118">İse, çalışma zamanı ayıklayıcıya keser.</span><span class="sxs-lookup"><span data-stu-id="39838-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="39838-119">Hata ayıklayıcı devam ettiğinde, ana bilgisayar çağırır.</span><span class="sxs-lookup"><span data-stu-id="39838-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="39838-120">Hiçbir hata ayıklayıcısı ekli, çalışma zamanı çağırır `IActionOnCLREvent::OnEvent` ve bir işaretçi geçirir bir `MDAInfo` örneği `data` parametresi.</span><span class="sxs-lookup"><span data-stu-id="39838-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="39838-121">Ana bilgisayar Mda'lar etkinleştirmek için ve bir MDA etkinleştirildiğinde uyarılmayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39838-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="39838-122">Bu konak varsayılan davranışı geçersiz kılma ve işlem durumunda bozulmasını önlemek için, olayı yönetilen iş parçacığı iptal etmek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="39838-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="39838-123">Mda'lar kullanma hakkında daha fazla bilgi için bkz: [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="39838-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39838-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39838-124">Requirements</span></span>  
 <span data-ttu-id="39838-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39838-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39838-126">**Başlık:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="39838-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="39838-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="39838-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39838-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39838-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39838-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39838-129">See Also</span></span>  
 [<span data-ttu-id="39838-130">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="39838-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="39838-131">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="39838-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

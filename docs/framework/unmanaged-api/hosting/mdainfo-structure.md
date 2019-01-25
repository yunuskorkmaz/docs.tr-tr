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
ms.openlocfilehash: 2d48c3d701b0369ab00150625c26d94f4111b2d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607218"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="6c89c-102">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c89c-102">MDAInfo Structure</span></span>
<span data-ttu-id="6c89c-103">Hakkında ayrıntılar sağlar `Event_MDAFired` olayı yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikler.</span><span class="sxs-lookup"><span data-stu-id="6c89c-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c89c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c89c-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="6c89c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6c89c-105">Members</span></span>  
  
|<span data-ttu-id="6c89c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6c89c-106">Member</span></span>|<span data-ttu-id="6c89c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c89c-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="6c89c-108">Geçerli MDA'ın başlığı.</span><span class="sxs-lookup"><span data-stu-id="6c89c-108">The title of the current MDA.</span></span> <span data-ttu-id="6c89c-109">Başlık tetiklenen hata türünü açıklar `Event_MDAFired` olay.</span><span class="sxs-lookup"><span data-stu-id="6c89c-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="6c89c-110">Geçerli bir MDA tarafından sağlanan çıkış iletisi.</span><span class="sxs-lookup"><span data-stu-id="6c89c-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c89c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c89c-111">Remarks</span></span>  
 <span data-ttu-id="6c89c-112">Yönetilen hata ayıklama Yardımcıları (MDAs) çalışma zamanı yürütme altyapısı, ortak dil çalışma zamanı (CLR) geçersiz koşulları belirleme gibi görevleri gerçekleştirmek için birlikte çalışan yardımlarda hata veya durumu hakkında ek bilgi dökümü alma altyapısı.</span><span class="sxs-lookup"><span data-stu-id="6c89c-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="6c89c-113">Mda'leri, aksi takdirde tuzak zor olan olaylar hakkında XML iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c89c-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="6c89c-114">Bunlar, yönetilen ve yönetilmeyen kod arasındaki geçişleri hata ayıklama için özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="6c89c-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="6c89c-115">Bir MDA oluşturulmasını tetikleyen bir olay harekete çalışma zamanı, aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="6c89c-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
-   <span data-ttu-id="6c89c-116">Konak kayıtlı değil, bir [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) çağırarak örneği [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) haberdar için bir `Event_MDAFired` çalışma zamanı olayı geçer ile kendi Varsayılan, barındırılan olmayan davranış.</span><span class="sxs-lookup"><span data-stu-id="6c89c-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
-   <span data-ttu-id="6c89c-117">Bu olay işleyicisi ana bilgisayarı kaydedildiyse, çalışma zamanı hata ayıklayıcı işleme ekli olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="6c89c-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="6c89c-118">Bu durumda, çalışma zamanı hata ayıklayıcıya keser.</span><span class="sxs-lookup"><span data-stu-id="6c89c-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="6c89c-119">Hata ayıklayıcının devam ettiğinde, ana bilgisayar çağırır.</span><span class="sxs-lookup"><span data-stu-id="6c89c-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="6c89c-120">Hata ayıklayıcı bağlıysa, çalışma zamanı çağırır `IActionOnCLREvent::OnEvent` ve işaretçi bir `MDAInfo` örneği `data` parametresi.</span><span class="sxs-lookup"><span data-stu-id="6c89c-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="6c89c-121">Mda'leri etkinleştirme ve bir MDA etkinleştirildiğinde bildirim almak için konağı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c89c-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="6c89c-122">Bu konak varsayılan davranışı geçersiz kılabilir ve işlem durumu bozan gelen önlemek için olayı tetikleyen yönetilen iş parçacığını durdurmak için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c89c-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="6c89c-123">Mda'leri kullanma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="6c89c-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c89c-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c89c-124">Requirements</span></span>  
 <span data-ttu-id="6c89c-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c89c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c89c-126">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="6c89c-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="6c89c-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6c89c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c89c-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c89c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c89c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c89c-129">See also</span></span>
- [<span data-ttu-id="6c89c-130">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="6c89c-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="6c89c-131">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="6c89c-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

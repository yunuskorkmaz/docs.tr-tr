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
ms.openlocfilehash: faa6af54714f7f0b7ac91c7836673c163195d5f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656465"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="989e1-102">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="989e1-102">MDAInfo Structure</span></span>
<span data-ttu-id="989e1-103">Hakkında ayrıntılar sağlar `Event_MDAFired` olayı yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikler.</span><span class="sxs-lookup"><span data-stu-id="989e1-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="989e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="989e1-104">Syntax</span></span>  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="989e1-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="989e1-105">Members</span></span>  
  
|<span data-ttu-id="989e1-106">Üye</span><span class="sxs-lookup"><span data-stu-id="989e1-106">Member</span></span>|<span data-ttu-id="989e1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="989e1-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="989e1-108">Geçerli MDA'ın başlığı.</span><span class="sxs-lookup"><span data-stu-id="989e1-108">The title of the current MDA.</span></span> <span data-ttu-id="989e1-109">Başlık tetiklenen hata türünü açıklar `Event_MDAFired` olay.</span><span class="sxs-lookup"><span data-stu-id="989e1-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="989e1-110">Geçerli bir MDA tarafından sağlanan çıkış iletisi.</span><span class="sxs-lookup"><span data-stu-id="989e1-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="989e1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="989e1-111">Remarks</span></span>  
 <span data-ttu-id="989e1-112">Yönetilen hata ayıklama Yardımcıları (MDAs) çalışma zamanı yürütme altyapısı, ortak dil çalışma zamanı (CLR) geçersiz koşulları belirleme gibi görevleri gerçekleştirmek için birlikte çalışan yardımlarda hata veya durumu hakkında ek bilgi dökümü alma altyapısı.</span><span class="sxs-lookup"><span data-stu-id="989e1-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="989e1-113">Mda'leri, aksi takdirde tuzak zor olan olaylar hakkında XML iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="989e1-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="989e1-114">Bunlar, yönetilen ve yönetilmeyen kod arasındaki geçişleri hata ayıklama için özellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="989e1-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="989e1-115">Bir MDA oluşturulmasını tetikleyen bir olay harekete çalışma zamanı, aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="989e1-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="989e1-116">Konak kayıtlı değil, bir [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) çağırarak örneği [Iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) haberdar için bir `Event_MDAFired` çalışma zamanı olayı geçer ile kendi Varsayılan, barındırılan olmayan davranış.</span><span class="sxs-lookup"><span data-stu-id="989e1-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="989e1-117">Bu olay işleyicisi ana bilgisayarı kaydedildiyse, çalışma zamanı hata ayıklayıcı işleme ekli olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="989e1-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="989e1-118">Bu durumda, çalışma zamanı hata ayıklayıcıya keser.</span><span class="sxs-lookup"><span data-stu-id="989e1-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="989e1-119">Hata ayıklayıcının devam ettiğinde, ana bilgisayar çağırır.</span><span class="sxs-lookup"><span data-stu-id="989e1-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="989e1-120">Hata ayıklayıcı bağlıysa, çalışma zamanı çağırır `IActionOnCLREvent::OnEvent` ve işaretçi bir `MDAInfo` örneği `data` parametresi.</span><span class="sxs-lookup"><span data-stu-id="989e1-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="989e1-121">Mda'leri etkinleştirme ve bir MDA etkinleştirildiğinde bildirim almak için konağı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="989e1-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="989e1-122">Bu konak varsayılan davranışı geçersiz kılabilir ve işlem durumu bozan gelen önlemek için olayı tetikleyen yönetilen iş parçacığını durdurmak için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="989e1-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="989e1-123">Mda'leri kullanma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="989e1-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="989e1-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="989e1-124">Requirements</span></span>  
 <span data-ttu-id="989e1-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="989e1-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="989e1-126">**Üst bilgi:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="989e1-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="989e1-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="989e1-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="989e1-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="989e1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="989e1-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="989e1-129">See also</span></span>

- [<span data-ttu-id="989e1-130">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="989e1-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="989e1-131">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="989e1-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

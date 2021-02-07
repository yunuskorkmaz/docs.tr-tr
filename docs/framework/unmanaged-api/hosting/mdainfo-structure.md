---
description: 'Daha fazla bilgi edinin: Mdadınfo yapısı'
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
ms.openlocfilehash: 5c42537a68d38e6cff3d70dcb796cd733ce64a1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679764"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="127f9-103">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="127f9-103">MDAInfo Structure</span></span>

<span data-ttu-id="127f9-104">`Event_MDAFired`Yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikleyen olayla ilgili ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="127f9-104">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="127f9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="127f9-105">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="127f9-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="127f9-106">Members</span></span>  
  
|<span data-ttu-id="127f9-107">Üye</span><span class="sxs-lookup"><span data-stu-id="127f9-107">Member</span></span>|<span data-ttu-id="127f9-108">Description</span><span class="sxs-lookup"><span data-stu-id="127f9-108">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="127f9-109">Geçerli MDA 'ın başlığı.</span><span class="sxs-lookup"><span data-stu-id="127f9-109">The title of the current MDA.</span></span> <span data-ttu-id="127f9-110">Başlık, olayı tetikleyen hata türünü açıklar `Event_MDAFired` .</span><span class="sxs-lookup"><span data-stu-id="127f9-110">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="127f9-111">Geçerli MDA tarafından sunulan çıkış iletisi.</span><span class="sxs-lookup"><span data-stu-id="127f9-111">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="127f9-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="127f9-112">Remarks</span></span>  

 <span data-ttu-id="127f9-113">Yönetilen hata ayıklama yardımcıları (MDAs), çalışma zamanı yürütme altyapısında geçersiz koşulları tanımlama veya altyapının durumu hakkında ek bilgi dökümü gibi görevleri gerçekleştirmek için ortak dil çalışma zamanı (CLR) ile birlikte çalışan hata ayıklama yardımlarıdır.</span><span class="sxs-lookup"><span data-stu-id="127f9-113">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="127f9-114">MDAs, tuzak zor olan olaylar hakkında XML iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="127f9-114">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="127f9-115">Yönetilen ve yönetilmeyen kod arasındaki geçişlerde hata ayıklama için özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="127f9-115">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="127f9-116">Çalışma zamanı, bir MDA öğesinin oluşturulmasını tetikleyen bir olay harekete geçirildiğinde aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="127f9-116">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="127f9-117">Ana bilgisayar bir olay hakkında bildirim almak için [ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) öğesini çağırarak bir [IActionOnCLREvent](iactiononclrevent-interface.md) örneği kaydettirmemişse `Event_MDAFired` , çalışma zamanı varsayılan, barındırılmamış davranışıyla devam eder.</span><span class="sxs-lookup"><span data-stu-id="127f9-117">If the host has not registered an [IActionOnCLREvent](iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="127f9-118">Konakta bu olay için bir işleyici kaydedilmişse, çalışma zamanı bir hata ayıklayıcının işleme bağlı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="127f9-118">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="127f9-119">Eğer ise, çalışma zamanı hata ayıklayıcıya kesilir.</span><span class="sxs-lookup"><span data-stu-id="127f9-119">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="127f9-120">Hata ayıklayıcı devam ederse, ana bilgisayara çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="127f9-120">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="127f9-121">Herhangi bir hata ayıklayıcı ekli değilse, çalışma zamanı bir `IActionOnCLREvent::OnEvent` örneğe bir işaretçi çağırır ve bir işaretçiyi `MDAInfo` parametre olarak geçirir `data` .</span><span class="sxs-lookup"><span data-stu-id="127f9-121">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="127f9-122">Ana bilgisayar Mdaları etkinleştirmeyi seçebilir ve bir MDA etkinleştirildiğinde bildirim alabilir.</span><span class="sxs-lookup"><span data-stu-id="127f9-122">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="127f9-123">Bu, ana bilgisayara varsayılan davranışı geçersiz kılmak ve olayı oluşturan yönetilen iş parçacığını durdurmak için, işlem durumunu bozmasını engellemek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="127f9-123">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="127f9-124">MDAs kullanma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="127f9-124">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="127f9-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="127f9-125">Requirements</span></span>  

 <span data-ttu-id="127f9-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="127f9-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="127f9-127">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="127f9-127">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="127f9-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="127f9-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="127f9-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="127f9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127f9-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="127f9-130">See also</span></span>

- [<span data-ttu-id="127f9-131">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="127f9-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="127f9-132">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="127f9-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

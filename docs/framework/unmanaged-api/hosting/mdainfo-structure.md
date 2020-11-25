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
ms.openlocfilehash: 8e88d90e3291d21888fae7aa162f84b6377658c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730025"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="fac88-102">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="fac88-102">MDAInfo Structure</span></span>

<span data-ttu-id="fac88-103">`Event_MDAFired`Yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikleyen olayla ilgili ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="fac88-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac88-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fac88-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="fac88-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fac88-105">Members</span></span>  
  
|<span data-ttu-id="fac88-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fac88-106">Member</span></span>|<span data-ttu-id="fac88-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fac88-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="fac88-108">Geçerli MDA 'ın başlığı.</span><span class="sxs-lookup"><span data-stu-id="fac88-108">The title of the current MDA.</span></span> <span data-ttu-id="fac88-109">Başlık, olayı tetikleyen hata türünü açıklar `Event_MDAFired` .</span><span class="sxs-lookup"><span data-stu-id="fac88-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="fac88-110">Geçerli MDA tarafından sunulan çıkış iletisi.</span><span class="sxs-lookup"><span data-stu-id="fac88-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fac88-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fac88-111">Remarks</span></span>  

 <span data-ttu-id="fac88-112">Yönetilen hata ayıklama yardımcıları (MDAs), çalışma zamanı yürütme altyapısında geçersiz koşulları tanımlama veya altyapının durumu hakkında ek bilgi dökümü gibi görevleri gerçekleştirmek için ortak dil çalışma zamanı (CLR) ile birlikte çalışan hata ayıklama yardımlarıdır.</span><span class="sxs-lookup"><span data-stu-id="fac88-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="fac88-113">MDAs, tuzak zor olan olaylar hakkında XML iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fac88-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="fac88-114">Yönetilen ve yönetilmeyen kod arasındaki geçişlerde hata ayıklama için özellikle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="fac88-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="fac88-115">Çalışma zamanı, bir MDA öğesinin oluşturulmasını tetikleyen bir olay harekete geçirildiğinde aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="fac88-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="fac88-116">Ana bilgisayar bir olay hakkında bildirim almak için [ICLROnEventManager:: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) öğesini çağırarak bir [IActionOnCLREvent](iactiononclrevent-interface.md) örneği kaydettirmemişse `Event_MDAFired` , çalışma zamanı varsayılan, barındırılmamış davranışıyla devam eder.</span><span class="sxs-lookup"><span data-stu-id="fac88-116">If the host has not registered an [IActionOnCLREvent](iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="fac88-117">Konakta bu olay için bir işleyici kaydedilmişse, çalışma zamanı bir hata ayıklayıcının işleme bağlı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="fac88-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="fac88-118">Eğer ise, çalışma zamanı hata ayıklayıcıya kesilir.</span><span class="sxs-lookup"><span data-stu-id="fac88-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="fac88-119">Hata ayıklayıcı devam ederse, ana bilgisayara çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="fac88-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="fac88-120">Herhangi bir hata ayıklayıcı ekli değilse, çalışma zamanı bir `IActionOnCLREvent::OnEvent` örneğe bir işaretçi çağırır ve bir işaretçiyi `MDAInfo` parametre olarak geçirir `data` .</span><span class="sxs-lookup"><span data-stu-id="fac88-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="fac88-121">Ana bilgisayar Mdaları etkinleştirmeyi seçebilir ve bir MDA etkinleştirildiğinde bildirim alabilir.</span><span class="sxs-lookup"><span data-stu-id="fac88-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="fac88-122">Bu, ana bilgisayara varsayılan davranışı geçersiz kılmak ve olayı oluşturan yönetilen iş parçacığını durdurmak için, işlem durumunu bozmasını engellemek için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="fac88-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="fac88-123">MDAs kullanma hakkında daha fazla bilgi için bkz. [yönetilen hata ayıklama yardımcıları Ile hataları tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="fac88-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fac88-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fac88-124">Requirements</span></span>  

 <span data-ttu-id="fac88-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fac88-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fac88-126">**Üst bilgi:** MSCorEE. IDL</span><span class="sxs-lookup"><span data-stu-id="fac88-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="fac88-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fac88-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fac88-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fac88-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac88-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fac88-129">See also</span></span>

- [<span data-ttu-id="fac88-130">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="fac88-130">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="fac88-131">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="fac88-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

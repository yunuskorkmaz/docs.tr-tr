---
description: 'Daha fazla bilgi edinin: EClrOperation numaralandırması'
title: EClrOperation Numaralandırması
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
ms.openlocfilehash: 9f75762a400955b5f36fb2a337f283e36a32658c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785568"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="af152-103">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="af152-103">EClrOperation Enumeration</span></span>

<span data-ttu-id="af152-104">Bir konağın ilke eylemlerini uygulayabileceği işlemler kümesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="af152-104">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af152-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="af152-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a><span data-ttu-id="af152-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="af152-106">Members</span></span>  
  
|<span data-ttu-id="af152-107">Üye</span><span class="sxs-lookup"><span data-stu-id="af152-107">Member</span></span>|<span data-ttu-id="af152-108">Description</span><span class="sxs-lookup"><span data-stu-id="af152-108">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="af152-109">Ana bilgisayar, <xref:System.AppDomain> normal olmayan (Rude) bir biçimde kaldırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="af152-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="af152-110">Ana bilgisayar, kaldırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="af152-110">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="af152-111">Konak, sonlandırıcılar çalıştırıldığında gerçekleştirilecek ilke eylemlerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="af152-111">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="af152-112">Ana bilgisayar, işlem çıktığında gerçekleştirilecek ilke eylemlerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="af152-112">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="af152-113">Konak, bir iş parçacığı iptal edildiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="af152-113">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="af152-114">Ana bilgisayar, kritik kod bölgesinde bir işlenmemiş iş parçacığı iptali gerçekleştiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="af152-114">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="af152-115">Ana bilgisayar kritik olmayan bir kod bölgesinde bir işlenmemiş iş parçacığı iptali gerçekleştiğinde gerçekleştirilecek ilke eylemlerini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="af152-115">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af152-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af152-116">Remarks</span></span>  

 <span data-ttu-id="af152-117">Ortak dil çalışma zamanı (CLR) güvenilirlik altyapısı, kod ve kritik olmayan kod bölgelerinde oluşan önemli bölgelerde oluşan iptal ve kaynak ayırma arızalarını birbirinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="af152-117">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="af152-118">Bu ayrım, ana bilgisayarların kodda bir hatanın oluştuğu yere bağlı olarak farklı ilkeler değiştirmesine izin vermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="af152-118">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="af152-119">*Kritik kod bölgesi* , clr 'nin bir görevi iptal etme veya kaynakların bir isteği tamamlayamamakta olduğunu garanti edemediği, yalnızca geçerli görevi etkilediği bir alandır.</span><span class="sxs-lookup"><span data-stu-id="af152-119">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="af152-120">Örneğin, bir görev bir kilit tutuyor ve bir bellek ayırma isteği yapıldığında hata belirten bir HRESULT alırsa, ' nin kararlılığını sağlamak için bu görevi durdurmak yeterli değildir <xref:System.AppDomain> çünkü, <xref:System.AppDomain> aynı kilidi bekleyen diğer görevleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="af152-120">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="af152-121">Geçerli görevi bırakmak için diğer görevlerin yanıt vermemesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="af152-121">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="af152-122">Böyle bir durumda, konağın <xref:System.AppDomain> risk olası dengesizinden değil, tümünü kaldırma yeteneği olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="af152-122">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="af152-123">Diğer taraftan, *kritik olmayan bir kod bölgesi*, clr 'nin bir iptal ya da bir başarısızlığın yalnızca hatanın gerçekleştiği görevi etkileyeceğini garanti edebildiği bir bölgedir.</span><span class="sxs-lookup"><span data-stu-id="af152-123">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="af152-124">CLR, düzgün kapanma ve düzgün olmayan (Rude) kaldırma işlemini de ayırt eder.</span><span class="sxs-lookup"><span data-stu-id="af152-124">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="af152-125">Genel olarak, normal veya düzgün bir şekilde iptali, bir görevi iptal etmeden önce özel durum işleme yordamlarını ve sonlandırıcıları çalıştırma çabalarının yanı sıra bir işlenmemiş iptali bu tür garantiyi yapmaz.</span><span class="sxs-lookup"><span data-stu-id="af152-125">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af152-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af152-126">Requirements</span></span>  

 <span data-ttu-id="af152-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af152-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af152-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="af152-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af152-129">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af152-129">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af152-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af152-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af152-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af152-131">See also</span></span>

- [<span data-ttu-id="af152-132">EClrFailure Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="af152-132">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="af152-133">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="af152-133">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="af152-134">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af152-134">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="af152-135">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af152-135">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="af152-136">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="af152-136">Hosting Enumerations</span></span>](hosting-enumerations.md)

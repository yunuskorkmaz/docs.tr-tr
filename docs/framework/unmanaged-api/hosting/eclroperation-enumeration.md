---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b18c89cee0c3f5088a9978e448a0d61de1b9848
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434251"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="c5eeb-102">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c5eeb-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="c5eeb-103">Bir ana bilgisayar ilkesi eylemleri uygulayabilirsiniz işlemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5eeb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5eeb-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="c5eeb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c5eeb-105">Members</span></span>  
  
|<span data-ttu-id="c5eeb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c5eeb-106">Member</span></span>|<span data-ttu-id="c5eeb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5eeb-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="c5eeb-108">Ana bilgisayar ilkesi olduğunda gerçekleştirilecek eylemleri belirtebilirsiniz bir <xref:System.AppDomain> (utangaç) normal olmayan bir şekilde kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="c5eeb-109">Ana bilgisayar ilkesi olduğunda gerçekleştirilecek eylemleri belirtebilirsiniz bir <xref:System.AppDomain> kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="c5eeb-110">Ana bilgisayar ilkesi sonlandırıcılar çalıştırdığınızda, gerçekleştirilecek eylemleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="c5eeb-111">Ana bilgisayar ilkesi işlem çıktığında gerçekleştirilecek eylemleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="c5eeb-112">Ana bilgisayar ilkesi bir iş parçacığı iptal edildiğinde gerçekleştirilecek eylemleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="c5eeb-113">Ana bilgisayar ilkesi utangaç iş parçacığı iptal kod kritik bir bölgede olduğunda gerçekleştirilecek eylemleri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="c5eeb-114">Ana bilgisayar olması utangaç iş parçacığı iptal kod kritik olmayan bir bölgede oluştuğunda İlkesi eylemler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5eeb-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5eeb-115">Remarks</span></span>  
 <span data-ttu-id="c5eeb-116">Ortak dil çalışma zamanı (CLR) güvenilirlik altyapısının iptal eder ve kaynak arasında kodu ve kod kritik olmayan bölgelerde ortaya kritik bölgelerdeki oluşan ayırma hatalarını ayırır.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="c5eeb-117">Bu ayrım kodda bir hata oluştuğu bağlı olarak farklı ilkeleri ayarlamak ana izin verecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="c5eeb-118">A *kritik bölge kodu* burada CLR garanti etmez, bir görevi iptal etme veya kaynakları yalnızca geçerli görev etkiler için bir isteği tamamlamak başarısız olan herhangi bir alandır.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="c5eeb-119">Bir görev bir kilit ve bellek ayırma isteği yaptıktan sonra hata olduğunu gösteren bir HRESULT alır, örneğin, bunu yalnızca kararlılığını emin olmak için bu görev iptal etmek yeterli değil <xref:System.AppDomain>, çünkü <xref:System.AppDomain> diğer içerebilir aynı kilidi için bekleyen görevler.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="c5eeb-120">Geçerli bırakmasını görev olanlar yanıt vermemesine (veya askıda) diğer görevlerin neden olabilecek süresiz olarak.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-120">To abandon the current task might cause those other tasks to stop responding (or hang) indefinitely.</span></span> <span data-ttu-id="c5eeb-121">Böyle bir durumda, konak tüm kaldırma yeteneği gereken <xref:System.AppDomain> risk olası kararsızlığı yerine.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="c5eeb-122">A *kritik olmayan bölge kodu*, diğer yandan, burada CLR ise bir durdurma veya bir hata yalnızca hata oluştuğu görev etkiler bir bölgedir.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="c5eeb-123">CLR de normal ve normal olmayan (utangaç) iptalleri arasında ayırır.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="c5eeb-124">Genel olarak, normal veya normal iptal utangaç durdurma gibi garanti yaparken bir görevi iptal etmeden önce özel durum işleme rutinleri ve sonlandırıcılar çalıştırmak için her türlü çabayı göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5eeb-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5eeb-125">Requirements</span></span>  
 <span data-ttu-id="c5eeb-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5eeb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5eeb-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5eeb-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5eeb-128">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5eeb-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5eeb-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5eeb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5eeb-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5eeb-130">See Also</span></span>  
 [<span data-ttu-id="c5eeb-131">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c5eeb-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="c5eeb-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c5eeb-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="c5eeb-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5eeb-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="c5eeb-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5eeb-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="c5eeb-135">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c5eeb-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

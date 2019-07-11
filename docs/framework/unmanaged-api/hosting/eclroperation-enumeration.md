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
ms.openlocfilehash: 01b000ed3d75ddb6a7882cb8f03ff2cec64fb9fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767881"
---
# <a name="eclroperation-enumeration"></a><span data-ttu-id="ed41b-102">EClrOperation Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ed41b-102">EClrOperation Enumeration</span></span>
<span data-ttu-id="ed41b-103">Bir ana bilgisayar ilkesi eylemleri uygulayabilirsiniz işlemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="ed41b-103">Describes the set of operations for which a host can apply policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed41b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed41b-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ed41b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ed41b-105">Members</span></span>  
  
|<span data-ttu-id="ed41b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ed41b-106">Member</span></span>|<span data-ttu-id="ed41b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed41b-107">Description</span></span>|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|<span data-ttu-id="ed41b-108">Ne zaman gerçekleştirilecek eylemleri ilke belirtebilir bir <xref:System.AppDomain> (rude) normal olmayan bir şekilde kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="ed41b-108">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded in a non-graceful (rude) manner.</span></span>|  
|`OPR_AppDomainUnload`|<span data-ttu-id="ed41b-109">Ne zaman gerçekleştirilecek eylemleri ilke belirtebilir bir <xref:System.AppDomain> kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="ed41b-109">The host can specify policy actions to be taken when an <xref:System.AppDomain> is unloaded.</span></span>|  
|`OPR_FinalizerRun`|<span data-ttu-id="ed41b-110">Konak sonlandırıcılar çalıştırdığınızda, gerçekleştirilecek eylemleri İlkesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-110">The host can specify policy actions to be taken when finalizers run.</span></span>|  
|`OPR_ProcessExit`|<span data-ttu-id="ed41b-111">Ana bilgisayar işlemi olduğunda gerçekleştirilecek eylemleri İlkesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-111">The host can specify policy actions to be taken when the process exits.</span></span>|  
|`OPR_ThreadAbort`|<span data-ttu-id="ed41b-112">Konak, bir iş parçacığı durduruldu olduğunda gerçekleştirilecek eylemleri İlkesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-112">The host can specify policy actions to be taken when a thread is aborted.</span></span>|  
|`OPR_ThreadRudeAbortInCriticalRegion`|<span data-ttu-id="ed41b-113">Konak rude iş parçacığı durdurma kodu kritik bir bölgede olduğunda gerçekleştirilecek eylemleri İlkesi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-113">The host can specify policy actions to be taken when a rude thread abort occurs in a critical region of code.</span></span>|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|<span data-ttu-id="ed41b-114">Ana bilgisayar olması kritik olmayan bir kod bölgede rude iş parçacığı iptal ortaya çıktığında ilke eylemler belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-114">The host can specify policy actions to be take when a rude thread abort occurs in a non-critical region of code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed41b-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed41b-115">Remarks</span></span>  
 <span data-ttu-id="ed41b-116">Ortak dil çalışma zamanı (CLR) güvenilirlik altyapısı iptal eder ve kaynak arasında kritik bölge kodu ve kod kritik olmayan bölgelerde ortaya oluşan ayırma hatalarını ayırır.</span><span class="sxs-lookup"><span data-stu-id="ed41b-116">The common language runtime (CLR) reliability infrastructure distinguishes between aborts and resource allocation failures that occur in critical regions of code and those that occur in non-critical regions of code.</span></span> <span data-ttu-id="ed41b-117">Bu ayrım, bir hata kodu nerede oluştuğunu bağlı olarak farklı ilkeleri ayarlamak konakları izin vermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ed41b-117">This distinction is designed to allow hosts to set different policies depending on where a failure occurs in the code.</span></span>  
  
 <span data-ttu-id="ed41b-118">A *kritik bölge kodu* herhangi alanı burada CLR garanti etmez, bir görevi iptal etme veya şu anki görevini kaynakları etkiler isteği tamamlayamıyor.</span><span class="sxs-lookup"><span data-stu-id="ed41b-118">A *critical region of code* is any space where the CLR cannot guarantee that aborting a task or failing to complete a request for resources will affect only the current task.</span></span> <span data-ttu-id="ed41b-119">Bir görev bir kilit ve bellek ayırma isteği yapan bağlı hata olduğunu gösteren bir HRESULT alır, örneğin, bu yalnızca kararlılığını emin olmak için bu görevi iptal etmek yetersizdir <xref:System.AppDomain>, çünkü <xref:System.AppDomain> diğer içerebilir aynı kilit için bekleyen görevler.</span><span class="sxs-lookup"><span data-stu-id="ed41b-119">For example, if a task is holding a lock and receives an HRESULT that indicates failure upon making a memory allocation request, it is insufficient simply to abort that task to ensure the stability of the <xref:System.AppDomain>, because the <xref:System.AppDomain> might contain other tasks waiting for the same lock.</span></span> <span data-ttu-id="ed41b-120">Görev geçerli iptal etmek için bu diğer görevlerin yanıt vermeyi durdurmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed41b-120">To abandon the current task might cause those other tasks to stop responding.</span></span> <span data-ttu-id="ed41b-121">Böyle bir durumda, konak tüm kaldırma yeteneği olması gerekir. <xref:System.AppDomain> risk olası kararsızlığı yerine.</span><span class="sxs-lookup"><span data-stu-id="ed41b-121">In such a case, the host needs the ability to unload the entire <xref:System.AppDomain> rather than risk potential instability.</span></span>  
  
 <span data-ttu-id="ed41b-122">A *kritik olmayan bölge kodu*, diğer taraftan, CLR burada garanti yalnızca bağlı hata oluşursa görev bir iptal ya da başarısızlık etkiler bir bölgedir.</span><span class="sxs-lookup"><span data-stu-id="ed41b-122">A *non-critical region of code*, on the other hand, is a region where the CLR can guarantee that an abort or a failure will affect only the task upon which the error occurs.</span></span>  
  
 <span data-ttu-id="ed41b-123">CLR ayrıca arasında düzgün ve başarılı olmayan (rude) iptalleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="ed41b-123">The CLR also distinguishes between graceful and non-graceful (rude) aborts.</span></span> <span data-ttu-id="ed41b-124">Genel olarak, normal veya normal iptal rude durdurma gibi garanti yaparken, bir görev iptal edilmeden önce özel durum işleme rutinleri ve sonlandırıcılar çalıştırmak için her türlü çabayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ed41b-124">In general, a normal or graceful abort makes every effort to run exception-handling routines and finalizers before aborting a task, while a rude abort makes no such guarantees.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed41b-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed41b-125">Requirements</span></span>  
 <span data-ttu-id="ed41b-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed41b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed41b-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ed41b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed41b-128">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ed41b-128">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed41b-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed41b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed41b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed41b-130">See also</span></span>

- [<span data-ttu-id="ed41b-131">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ed41b-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="ed41b-132">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ed41b-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="ed41b-133">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed41b-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="ed41b-134">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed41b-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="ed41b-135">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="ed41b-135">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

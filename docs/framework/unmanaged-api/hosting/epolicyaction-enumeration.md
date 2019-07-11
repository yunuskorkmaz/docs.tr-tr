---
title: EPolicyAction Numaralandırması
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 404cd5513a1cbd353faed41030a80ec2abef235f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774205"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="4fa15-102">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4fa15-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="4fa15-103">Ana bilgisayar tarafından açıklanan işlemleri için ayarlayabileceğiniz İlkesi eylemleri açıklar [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) ve hataları tarafından açıklanan [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="4fa15-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa15-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fa15-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a><span data-ttu-id="4fa15-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4fa15-105">Members</span></span>  
  
|<span data-ttu-id="4fa15-106">Üye</span><span class="sxs-lookup"><span data-stu-id="4fa15-106">Member</span></span>|<span data-ttu-id="4fa15-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fa15-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="4fa15-108">Ortak dil çalışma zamanı (CLR) iş parçacığı düzgün bir şekilde iptal belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="4fa15-109">Normal iptal tüm çalıştırma girişimlerini içerir `finally` engeller, tüm `catch` blokları, iş parçacığı iptalleri ve sonlandırıcılar ilgili.</span><span class="sxs-lookup"><span data-stu-id="4fa15-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="4fa15-110">CLR devre dışı durumuna girdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="4fa15-111">Yönetilen kod etkilenen işlemde başka yürütülebilecek ve iş parçacıkları CLR girmesini engellenir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="4fa15-112">CLR işleminin sonlandırıcılar çalıştırma ve temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme gibi normal bir çıkış denemesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="4fa15-113">CLR işlemi hemen sonlandırıcılar çalıştırma veya temizleme ve günlüğe kaydetme işlemlerini gerçekleştiren çıkış belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="4fa15-114">Ancak, bildirim hata ayıklayıcıya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="4fa15-115">Hiçbir işlem yapılmadı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="4fa15-116">CLR rude iş parçacığı iptal gerçekleştirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="4fa15-117">Yalnızca `catch` ve `finally` simgesiyle işaretli blok <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4fa15-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="4fa15-118">Sonlandırıcılar çalıştıran veya işlem günlüğü CLR işleminden çıkış olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="4fa15-119">CLR bir rude kaldırmaya gerçekleştirileceğini belirtir <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="4fa15-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="4fa15-120">Yalnızca bir sonlandırıcı işaretlenmiş <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4fa15-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="4fa15-121">Benzer şekilde, tüm iş parçacıkları bu <xref:System.AppDomain> almak, yığındaki bir `ThreadAbortException`, ancak yalnızca `catch` ve `finally` simgesiyle işaretli blok <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="4fa15-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="4fa15-122">Bellek yetersiz arabellek taşması ve benzeri, gibi koşula uygun bir özel durumun oluşturulmasını da belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="4fa15-123">Belirten <xref:System.AppDomain> kaldırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fa15-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="4fa15-124">CLR, sonlandırıcılar çalıştırmayı dener.</span><span class="sxs-lookup"><span data-stu-id="4fa15-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fa15-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fa15-125">Remarks</span></span>  
 <span data-ttu-id="4fa15-126">Ana bilgisayar ilkesi eylemleri yöntemleri çağırarak ayarlar [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4fa15-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="4fa15-127">İşlenmemiş ve normal iptal edilmesini hakkında daha fazla bilgi için bkz. [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="4fa15-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fa15-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fa15-128">Requirements</span></span>  
 <span data-ttu-id="4fa15-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fa15-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fa15-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4fa15-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fa15-131">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4fa15-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fa15-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fa15-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa15-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fa15-133">See also</span></span>

- [<span data-ttu-id="4fa15-134">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="4fa15-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="4fa15-135">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fa15-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="4fa15-136">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fa15-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="4fa15-137">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="4fa15-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

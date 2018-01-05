---
title: "EPolicyAction Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EPolicyAction
api_location: mscoree.dll
api_type: COM
f1_keywords: EPolicyAction
helpviewer_keywords: EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5de55d46eead37962fad7d7c1c5bd1766e772fe8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="b90d7-102">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b90d7-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="b90d7-103">Ana bilgisayar tarafından açıklanan işlemleri için ayarlayabileceğiniz ilke eylemleri açıklar [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) ve hataları tarafından açıklanan [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b90d7-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b90d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b90d7-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="b90d7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b90d7-105">Members</span></span>  
  
|<span data-ttu-id="b90d7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b90d7-106">Member</span></span>|<span data-ttu-id="b90d7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b90d7-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="b90d7-108">Ortak dil çalışma zamanı (CLR) iş parçacığı düzgün biçimde iptal belirtir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="b90d7-109">Tüm çalıştırma denemelerini normal iptal içeren `finally` engeller, herhangi bir `catch` blokları ilgili iş parçacığı iptalleri ve sonlandırıcılar.</span><span class="sxs-lookup"><span data-stu-id="b90d7-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="b90d7-110">CLR devre dışı durumuna girmelisiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="b90d7-111">Yönetilen kod etkilenen işleminde başka çalıştırılabilir ve iş parçacıkları CLR girmesini engellenir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="b90d7-112">CLR işleminin sonlandırıcılar çalıştırma ve temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme gibi normal bir çıkış denemesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="b90d7-113">CLR işlemi hemen sonlandırıcılar çalıştıran veya temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme çıkış belirtir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="b90d7-114">Nowever, hata ayıklayıcı için bildirim gönderilir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-114">Nowever, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="b90d7-115">Hiçbir işlem yapılmadı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="b90d7-116">CLR utangaç iş parçacığı iptal gerçekleştirileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="b90d7-117">Yalnızca `catch` ve `finally` blokları işaretlenmiş <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b90d7-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="b90d7-118">CLR sonlandırıcılar çalıştıran veya işlem günlüğü işlemi kapanmamalıdır belirtir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="b90d7-119">CLR, utangaç unload gerçekleştirileceğini belirtir <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="b90d7-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="b90d7-120">Yalnızca sonlandırıcılar işaretlenmiş <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b90d7-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="b90d7-121">Benzer şekilde, tüm iş parçacıklarını bu <xref:System.AppDomain> kendi yığınında alma bir `ThreadAbortException`, ancak yalnızca `catch` ve `finally` blokları işaretlenmiş <xref:System.EnterpriseServices.MustRunInClientContextAttribute> yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b90d7-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="b90d7-122">Bellek yetersiz arabellek taşması ve benzeri, gibi koşula uygun bir özel durum olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="b90d7-123">Belirleyen <xref:System.AppDomain> kaldırılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b90d7-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="b90d7-124">CLR sonlandırıcılar çalıştırmayı dener.</span><span class="sxs-lookup"><span data-stu-id="b90d7-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b90d7-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b90d7-125">Remarks</span></span>  
 <span data-ttu-id="b90d7-126">Ana bilgisayar ilkesi eylemleri yöntemlerini çağırarak ayarlar [Iclrpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b90d7-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="b90d7-127">Utangaç ve normal iptalleri hakkında daha fazla bilgi için bkz: [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b90d7-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b90d7-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b90d7-128">Requirements</span></span>  
 <span data-ttu-id="b90d7-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b90d7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b90d7-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b90d7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b90d7-131">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b90d7-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b90d7-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b90d7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90d7-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b90d7-133">See Also</span></span>  
 [<span data-ttu-id="b90d7-134">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b90d7-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="b90d7-135">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b90d7-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="b90d7-136">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b90d7-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [<span data-ttu-id="b90d7-137">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b90d7-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

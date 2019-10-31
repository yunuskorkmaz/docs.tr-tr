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
ms.openlocfilehash: eaba6b2166a82cfe825ffb98db515e24d4656462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138227"
---
# <a name="epolicyaction-enumeration"></a><span data-ttu-id="d7e22-102">EPolicyAction Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d7e22-102">EPolicyAction Enumeration</span></span>
<span data-ttu-id="d7e22-103">[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) tarafından tanımlanan Işlemler ve [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)tarafından tanımlanan hatalar için konağın ayarlayaşabilemeyen ilke eylemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7e22-103">Describes the policy actions the host can set for operations described by [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) and failures described by [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7e22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7e22-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d7e22-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d7e22-105">Members</span></span>  
  
|<span data-ttu-id="d7e22-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d7e22-106">Member</span></span>|<span data-ttu-id="d7e22-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7e22-107">Description</span></span>|  
|------------|-----------------|  
|`eAbortThread`|<span data-ttu-id="d7e22-108">Ortak dil çalışma zamanının (CLR) iş parçacığını düzgün bir şekilde iptal etmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-108">Specifies that the common language runtime (CLR) should abort the thread gracefully.</span></span> <span data-ttu-id="d7e22-109">Düzgün bir şekilde iptali, tüm `finally` blokları, iş parçacığı iptalleriyle ilgili tüm `catch` blokları ve sonlandırıcıları çalıştırma girişimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-109">A graceful abort includes attempts to run all `finally` blocks, any `catch` blocks related to thread aborts, and finalizers.</span></span>|  
|`eDisableRuntime`|<span data-ttu-id="d7e22-110">CLR 'nin devre dışı bir durum girmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-110">Specifies that the CLR should enter a disabled state.</span></span> <span data-ttu-id="d7e22-111">Etkilenen işlemde başka yönetilen kod yürütülemez ve iş parçacıklarının CLR 'ye girmaları engellenir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-111">No further managed code can be executed in the affected process, and threads are blocked from entering the CLR.</span></span>|  
|`eExitProcess`|<span data-ttu-id="d7e22-112">CLR 'nin, sonlandırıcıları çalıştırma ve temizleme ve günlüğe kaydetme işlemlerini gerçekleştirme dahil olmak üzere işlemden düzgün bir şekilde çıkış denemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-112">Specifies that the CLR should attempt a graceful exit of the process, including running finalizers and performing cleanup and logging operations.</span></span>|  
|`eFastExitProcess`|<span data-ttu-id="d7e22-113">CLR 'nin sonlandırıcıları çalıştırmadan veya temizleme ve günlüğe kaydetme işlemlerini gerçekleştirmeksizin işlemden hemen çıkış gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-113">Specifies that the CLR should exit the process immediately, without running finalizers or performing cleanup and logging operations.</span></span> <span data-ttu-id="d7e22-114">Ancak, bildirim hata ayıklayıcıya gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-114">However, notification is sent to the debugger.</span></span>|  
|`eNoAction`|<span data-ttu-id="d7e22-115">Hiçbir eylemin alıngerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-115">Specifies that no action should be taken.</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="d7e22-116">CLR 'nin bir işlenmemiş iş parçacığı iptali gerçekleştirmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-116">Specifies that the CLR should perform a rude thread abort.</span></span> <span data-ttu-id="d7e22-117">Yalnızca <xref:System.EnterpriseServices.MustRunInClientContextAttribute> işaretlenen `catch` ve `finally` blokları yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d7e22-117">Only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eRudeExitProcess`|<span data-ttu-id="d7e22-118">CLR 'nin sonlandırıcılar veya günlüğe kaydetme işlemlerini çalıştırmadan işlemden çıkması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-118">Specifies that the CLR should exit the process without running finalizers or logging operations.</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="d7e22-119">CLR 'nin <xref:System.AppDomain>bir işlenmemiş yüklemesini gerçekleştirmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-119">Specifies that the CLR should perform a rude unload of the <xref:System.AppDomain>.</span></span> <span data-ttu-id="d7e22-120">Yalnızca <xref:System.EnterpriseServices.MustRunInClientContextAttribute> ile işaretlenen sonlandırıcılar yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d7e22-120">Only finalizers marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span> <span data-ttu-id="d7e22-121">Benzer şekilde, yığındaki bu <xref:System.AppDomain> sahip tüm iş parçacıkları bir `ThreadAbortException`alır, ancak yalnızca <xref:System.EnterpriseServices.MustRunInClientContextAttribute> ile işaretlenen `catch` ve `finally` blokları yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d7e22-121">Similarly, all threads with this <xref:System.AppDomain> in their stack receive a `ThreadAbortException`, but only those `catch` and `finally` blocks marked with <xref:System.EnterpriseServices.MustRunInClientContextAttribute> are executed.</span></span>|  
|`eThrowException`|<span data-ttu-id="d7e22-122">Koşula uygun bir özel durum (örneğin, bellek dışı, arabellek taşması vb.) oluşturulması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-122">Specifies that an exception appropriate to the condition, such as out-of-memory, buffer overflow, and so forth, should be thrown.</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="d7e22-123"><xref:System.AppDomain> yüklemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7e22-123">Specifies that the <xref:System.AppDomain> should be unloaded.</span></span> <span data-ttu-id="d7e22-124">CLR sonlandırıcıları çalıştırmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="d7e22-124">The CLR attempts to run finalizers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7e22-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7e22-125">Remarks</span></span>  
 <span data-ttu-id="d7e22-126">Konak, [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) arabiriminin yöntemlerini çağırarak ilke eylemlerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d7e22-126">The host sets policy actions by calling methods of the [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface.</span></span> <span data-ttu-id="d7e22-127">İşlenmemiş ve düzgün kaldırma hakkında bilgi için bkz. [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="d7e22-127">For information about rude and graceful aborts, see the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7e22-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d7e22-128">Requirements</span></span>  
 <span data-ttu-id="d7e22-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7e22-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7e22-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d7e22-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7e22-131">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d7e22-131">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7e22-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7e22-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7e22-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7e22-133">See also</span></span>

- [<span data-ttu-id="d7e22-134">EClrFailure Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d7e22-134">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="d7e22-135">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7e22-135">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="d7e22-136">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d7e22-136">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="d7e22-137">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d7e22-137">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

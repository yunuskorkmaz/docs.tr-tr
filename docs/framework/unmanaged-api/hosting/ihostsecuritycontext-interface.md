---
title: IHostSecurityContext Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c2500f013584ef4722ceaaaee91d5db54991639
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439305"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="791a4-102">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="791a4-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="791a4-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar tarafından uygulanan güvenlik bağlamı bilgilerini korumak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="791a4-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="791a4-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="791a4-104">Methods</span></span>  
  
|<span data-ttu-id="791a4-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="791a4-105">Method</span></span>|<span data-ttu-id="791a4-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="791a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="791a4-107">Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="791a4-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="791a4-108">Bir kopyasını alır `IHostSecurityContext` örneği döndürdü çağrısından [Ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="791a4-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="791a4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="791a4-109">Remarks</span></span>  
 <span data-ttu-id="791a4-110">Bir ana iş parçacığı belirteçleri tüm kod erişimi CLR ve kullanıcı kodu tarafından kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="791a4-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="791a4-111">Bu tam güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemleri veya kısıtlı kod erişimi olan kod noktaları üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="791a4-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="791a4-112">`IHostSecurityContext` çalışma zamanı opak bu güvenlik bağlamı bilgileri yalıtır.</span><span class="sxs-lookup"><span data-stu-id="791a4-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="791a4-113">Bu bilgileri kullanarak çalışma zamanı yakalar `Capture`, ve iş parçacığı havuzu çalışan öğesi gönderme, sonlandırıcıyı yürütme ve modülü ve sınıf oluşturucular arasında taşır.</span><span class="sxs-lookup"><span data-stu-id="791a4-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="791a4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="791a4-114">Requirements</span></span>  
 <span data-ttu-id="791a4-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="791a4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="791a4-116">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="791a4-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="791a4-117">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="791a4-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="791a4-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="791a4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791a4-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="791a4-119">See Also</span></span>  
 [<span data-ttu-id="791a4-120">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="791a4-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="791a4-121">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="791a4-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="791a4-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="791a4-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

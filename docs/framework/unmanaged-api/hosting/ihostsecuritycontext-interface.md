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
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124039"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="c1eff-102">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1eff-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="c1eff-103">Ortak dil çalışma zamanı (CLR) ana bilgisayar tarafından uygulanan güvenlik bağlamını korumak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1eff-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1eff-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c1eff-104">Methods</span></span>  
  
|<span data-ttu-id="c1eff-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c1eff-105">Method</span></span>|<span data-ttu-id="c1eff-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1eff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1eff-107">Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1eff-107">Capture Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|<span data-ttu-id="c1eff-108">Bir kopyasını alır `IHostSecurityContext` örnek geri çağrısından [Ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="c1eff-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1eff-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1eff-109">Remarks</span></span>  
 <span data-ttu-id="c1eff-110">Bir konak CLR ve kullanıcı kodu tarafından iş parçacığı belirteçleri tüm kod erişimi denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1eff-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="c1eff-111">Bu eksiksiz güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemler veya kod noktaları kod kısıtlı erişimle üzerinden geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c1eff-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="c1eff-112">`IHostSecurityContext` çalışma zamanı için donuktur bu güvenlik bağlamı bilgileri yalıtır.</span><span class="sxs-lookup"><span data-stu-id="c1eff-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="c1eff-113">Bu bilgileri kullanarak, çalışma zamanı yakalar `Capture`, ve iş parçacığı havuzu alt öğe gönderme, sonlandırıcı yürütme ve modül ve sınıf oluşturucular arasında taşır.</span><span class="sxs-lookup"><span data-stu-id="c1eff-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1eff-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1eff-114">Requirements</span></span>  
 <span data-ttu-id="c1eff-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1eff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1eff-116">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1eff-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1eff-117">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c1eff-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1eff-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1eff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1eff-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1eff-119">See also</span></span>

- [<span data-ttu-id="c1eff-120">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1eff-120">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="c1eff-121">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1eff-121">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="c1eff-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c1eff-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

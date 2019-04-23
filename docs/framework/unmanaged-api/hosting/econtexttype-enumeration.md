---
title: EContextType Numaralandırması
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f3643bf4880532a46fe7f9f57b8077032013728
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118085"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="3934a-102">EContextType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3934a-102">EContextType Enumeration</span></span>
<span data-ttu-id="3934a-103">Güvenlik bağlamı şu anda yürütülen iş parçacığının açıklar.</span><span class="sxs-lookup"><span data-stu-id="3934a-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3934a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3934a-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="3934a-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3934a-105">Members</span></span>  
  
|<span data-ttu-id="3934a-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3934a-106">Member</span></span>|<span data-ttu-id="3934a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3934a-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="3934a-108">Ortak dil çalışma zamanı (CLR) çağıran sırada geçerli iş parçacığının içeriğine gösterir [Ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) yöntemi veya bir çağrıda CLR tarafından talep edilen içeriği [ Ihostsecuritymanager::setsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3934a-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="3934a-109">Ana bilgisayar çöp Toplayıcıya veya sınıf veya modül oluşturucuları gibi daha düşük ayrıcalıklara sahip bir bağlam gösterir.</span><span class="sxs-lookup"><span data-stu-id="3934a-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3934a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3934a-110">Remarks</span></span>  
 <span data-ttu-id="3934a-111">CLR birini sağlayan `EContextType` değerleri yapılan çağrıda bir parametre değeri olarak `IHostSecurityManager::GetSecurityContext` ve `IHostSecurityManager::SetSecurityContext` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3934a-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3934a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3934a-112">Requirements</span></span>  
 <span data-ttu-id="3934a-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3934a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3934a-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3934a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3934a-115">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3934a-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3934a-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3934a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3934a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3934a-117">See also</span></span>

- [<span data-ttu-id="3934a-118">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3934a-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="3934a-119">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3934a-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="3934a-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3934a-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

---
title: "EContextType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd068816c5a642a7a8230fc14045e3f43980936c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="781cd-102">EContextType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="781cd-102">EContextType Enumeration</span></span>
<span data-ttu-id="781cd-103">Şu anda yürütülen iş parçacığı güvenlik bağlamında açıklar.</span><span class="sxs-lookup"><span data-stu-id="781cd-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="781cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="781cd-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="781cd-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="781cd-105">Members</span></span>  
  
|<span data-ttu-id="781cd-106">Üye</span><span class="sxs-lookup"><span data-stu-id="781cd-106">Member</span></span>|<span data-ttu-id="781cd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="781cd-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="781cd-108">Ortak dil çalışma zamanı (CLR) çağırır aynı anda geçerli iş parçacığının bağlamda gösterir [Ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) yöntemi veya CLR yapılan bir çağrı tarafından istenen içeriği [ Ihostsecuritymanager::setsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="781cd-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="781cd-109">Üzerinde konak atık toplayıcı veya sınıf ya da modül oluşturucular gibi daha düşük ayrıcalıklara sahip bir bağlamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="781cd-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="781cd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="781cd-110">Remarks</span></span>  
 <span data-ttu-id="781cd-111">CLR birini sağlayan `EContextType` değerleri çağrılarında bir parametre değeri olarak `IHostSecurityManager::GetSecurityContext` ve `IHostSecurityManager::SetSecurityContext` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="781cd-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="781cd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="781cd-112">Requirements</span></span>  
 <span data-ttu-id="781cd-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="781cd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="781cd-114">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="781cd-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="781cd-115">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="781cd-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="781cd-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="781cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="781cd-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="781cd-117">See Also</span></span>  
 [<span data-ttu-id="781cd-118">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="781cd-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="781cd-119">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="781cd-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="781cd-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="781cd-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

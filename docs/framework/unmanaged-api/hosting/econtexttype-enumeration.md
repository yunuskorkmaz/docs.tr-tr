---
title: "EContextType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EContextType
api_location: mscoree.dll
api_type: COM
f1_keywords: EContextType
helpviewer_keywords: EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73e6e9a1f1118a524b86b3711c0c7a6af4777f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="b90c2-102">EContextType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b90c2-102">EContextType Enumeration</span></span>
<span data-ttu-id="b90c2-103">Şu anda yürütülen iş parçacığı güvenlik bağlamında açıklar.</span><span class="sxs-lookup"><span data-stu-id="b90c2-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b90c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b90c2-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="b90c2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b90c2-105">Members</span></span>  
  
|<span data-ttu-id="b90c2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b90c2-106">Member</span></span>|<span data-ttu-id="b90c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b90c2-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="b90c2-108">Ortak dil çalışma zamanı (CLR) çağırır aynı anda geçerli iş parçacığının bağlamda gösterir [Ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) yöntemi veya CLR yapılan bir çağrı tarafından istenen içeriği [ Ihostsecuritymanager::setsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b90c2-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="b90c2-109">Üzerinde konak atık toplayıcı veya sınıf ya da modül oluşturucular gibi daha düşük ayrıcalıklara sahip bir bağlamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b90c2-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b90c2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b90c2-110">Remarks</span></span>  
 <span data-ttu-id="b90c2-111">CLR birini sağlayan `EContextType` değerleri çağrılarında bir parametre değeri olarak `IHostSecurityManager::GetSecurityContext` ve `IHostSecurityManager::SetSecurityContext` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="b90c2-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b90c2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b90c2-112">Requirements</span></span>  
 <span data-ttu-id="b90c2-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b90c2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b90c2-114">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b90c2-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b90c2-115">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b90c2-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b90c2-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b90c2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b90c2-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b90c2-117">See Also</span></span>  
 [<span data-ttu-id="b90c2-118">Ihostsecuritycontext arabirimi</span><span class="sxs-lookup"><span data-stu-id="b90c2-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="b90c2-119">Ihostsecuritymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="b90c2-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="b90c2-120">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="b90c2-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

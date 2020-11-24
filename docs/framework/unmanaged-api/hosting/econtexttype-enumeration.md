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
ms.openlocfilehash: c6d1ace12bd07fa1f14c8570eca1f950a5c22be9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686338"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="f0d1f-102">EContextType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f0d1f-102">EContextType Enumeration</span></span>

<span data-ttu-id="f0d1f-103">Yürütülmekte olan iş parçacığının güvenlik bağlamını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f0d1f-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d1f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f0d1f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="f0d1f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f0d1f-105">Members</span></span>  
  
|<span data-ttu-id="f0d1f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f0d1f-106">Member</span></span>|<span data-ttu-id="f0d1f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0d1f-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="f0d1f-108">Ortak dil çalışma zamanı (CLR) için [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) metodunu çağıran ve [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) metoduna yapılan çağrıda CLR tarafından istenen bağlamı belirten geçerli iş parçacığındaki bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0d1f-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="f0d1f-109">Konağın çöp toplayıcı veya sınıf ya da modül oluşturucuları gibi daha düşük ayrıcalıklara sahip olduğu bir bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f0d1f-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0d1f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0d1f-110">Remarks</span></span>  

 <span data-ttu-id="f0d1f-111">CLR, `EContextType` ve yöntemlerine yapılan çağrılarında bir parametre değeri olarak değerlerden birini sağlar `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="f0d1f-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d1f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0d1f-112">Requirements</span></span>  

 <span data-ttu-id="f0d1f-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0d1f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0d1f-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0d1f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0d1f-115">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0d1f-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0d1f-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d1f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d1f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0d1f-117">See also</span></span>

- [<span data-ttu-id="f0d1f-118">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0d1f-118">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="f0d1f-119">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0d1f-119">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="f0d1f-120">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="f0d1f-120">Hosting Enumerations</span></span>](hosting-enumerations.md)

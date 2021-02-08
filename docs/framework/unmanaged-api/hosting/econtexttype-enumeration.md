---
description: 'Daha fazla bilgi edinin: EContextType numaralandırması'
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
ms.openlocfilehash: b7d6ddb385386bb0616a01ef6fcc432f2c925d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785542"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="6ba05-103">EContextType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6ba05-103">EContextType Enumeration</span></span>

<span data-ttu-id="6ba05-104">Yürütülmekte olan iş parçacığının güvenlik bağlamını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ba05-104">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ba05-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ba05-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="6ba05-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6ba05-106">Members</span></span>  
  
|<span data-ttu-id="6ba05-107">Üye</span><span class="sxs-lookup"><span data-stu-id="6ba05-107">Member</span></span>|<span data-ttu-id="6ba05-108">Description</span><span class="sxs-lookup"><span data-stu-id="6ba05-108">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="6ba05-109">Ortak dil çalışma zamanı (CLR) için [IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) metodunu çağıran ve [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) metoduna yapılan çağrıda CLR tarafından istenen bağlamı belirten geçerli iş parçacığındaki bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ba05-109">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="6ba05-110">Konağın çöp toplayıcı veya sınıf ya da modül oluşturucuları gibi daha düşük ayrıcalıklara sahip olduğu bir bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ba05-110">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ba05-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ba05-111">Remarks</span></span>  

 <span data-ttu-id="6ba05-112">CLR, `EContextType` ve yöntemlerine yapılan çağrılarında bir parametre değeri olarak değerlerden birini sağlar `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="6ba05-112">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ba05-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ba05-113">Requirements</span></span>  

 <span data-ttu-id="6ba05-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ba05-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ba05-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ba05-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ba05-116">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ba05-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ba05-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ba05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba05-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ba05-118">See also</span></span>

- [<span data-ttu-id="6ba05-119">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ba05-119">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="6ba05-120">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ba05-120">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="6ba05-121">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="6ba05-121">Hosting Enumerations</span></span>](hosting-enumerations.md)

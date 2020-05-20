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
ms.openlocfilehash: ceb68410e808bf7843149e3f05a39c7a98d0c000
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616300"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="0a837-102">EContextType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="0a837-102">EContextType Enumeration</span></span>
<span data-ttu-id="0a837-103">Yürütülmekte olan iş parçacığının güvenlik bağlamını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0a837-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a837-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0a837-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="0a837-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0a837-105">Members</span></span>  
  
|<span data-ttu-id="0a837-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0a837-106">Member</span></span>|<span data-ttu-id="0a837-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a837-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="0a837-108">Ortak dil çalışma zamanı (CLR) için [IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metodunu çağıran ve [IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) metoduna yapılan çağrıda CLR tarafından istenen bağlamı belirten geçerli iş parçacığındaki bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a837-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="0a837-109">Konağın çöp toplayıcı veya sınıf ya da modül oluşturucuları gibi daha düşük ayrıcalıklara sahip olduğu bir bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a837-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a837-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0a837-110">Remarks</span></span>  
 <span data-ttu-id="0a837-111">CLR, `EContextType` ve yöntemlerine yapılan çağrılarında bir parametre değeri olarak değerlerden birini sağlar `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="0a837-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a837-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a837-112">Requirements</span></span>  
 <span data-ttu-id="0a837-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a837-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a837-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0a837-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0a837-115">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0a837-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a837-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a837-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a837-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a837-117">See also</span></span>

- [<span data-ttu-id="0a837-118">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a837-118">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="0a837-119">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a837-119">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="0a837-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="0a837-120">Hosting Enumerations</span></span>](hosting-enumerations.md)

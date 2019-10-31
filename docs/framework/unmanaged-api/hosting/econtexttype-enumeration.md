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
ms.openlocfilehash: 5e82f542bdc364a52fc558e582134a7d8d554ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131153"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="6218b-102">EContextType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6218b-102">EContextType Enumeration</span></span>
<span data-ttu-id="6218b-103">Yürütülmekte olan iş parçacığının güvenlik bağlamını açıklar.</span><span class="sxs-lookup"><span data-stu-id="6218b-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6218b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6218b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="6218b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6218b-105">Members</span></span>  
  
|<span data-ttu-id="6218b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6218b-106">Member</span></span>|<span data-ttu-id="6218b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6218b-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="6218b-108">Ortak dil çalışma zamanı (CLR), [IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) metodunu çağıran ve [IHostSecurityManager:: SETSECURITYCONTEXT çağrısında CLR tarafından istenen bağlamı belirten geçerli iş parçacığındaki bağlamı gösterir. ](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6218b-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="6218b-109">Konağın çöp toplayıcı veya sınıf ya da modül oluşturucuları gibi daha düşük ayrıcalıklara sahip olduğu bir bağlamı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6218b-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6218b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6218b-110">Remarks</span></span>  
 <span data-ttu-id="6218b-111">CLR, `IHostSecurityManager::GetSecurityContext` ve `IHostSecurityManager::SetSecurityContext` yöntemlerine yapılan çağrılarında bir parametre değeri olarak `EContextType` değerlerinden birini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6218b-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6218b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6218b-112">Requirements</span></span>  
 <span data-ttu-id="6218b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6218b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6218b-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6218b-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6218b-115">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6218b-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6218b-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6218b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6218b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6218b-117">See also</span></span>

- [<span data-ttu-id="6218b-118">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6218b-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="6218b-119">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6218b-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="6218b-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6218b-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

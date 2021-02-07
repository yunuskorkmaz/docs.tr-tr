---
description: 'Şu konuda daha fazla bilgi edinin: IHostSecurityManager:: RevertToSelf yöntemi'
title: IHostSecurityManager::RevertToSelf Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
ms.openlocfilehash: f3488653bcb498c7521de0e368b33bc444967f21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671509"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="10ad4-103">IHostSecurityManager::RevertToSelf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10ad4-103">IHostSecurityManager::RevertToSelf Method</span></span>

<span data-ttu-id="10ad4-104">Geçerli Kullanıcı kimliğini kimliğe bürünme işlemini sonlandırır ve özgün iş parçacığı belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="10ad4-104">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ad4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="10ad4-105">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="10ad4-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10ad4-106">Return Value</span></span>  
  
|<span data-ttu-id="10ad4-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10ad4-107">HRESULT</span></span>|<span data-ttu-id="10ad4-108">Description</span><span class="sxs-lookup"><span data-stu-id="10ad4-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10ad4-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="10ad4-109">S_OK</span></span>|<span data-ttu-id="10ad4-110">`RevertToSelf` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="10ad4-110">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="10ad4-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10ad4-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10ad4-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="10ad4-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10ad4-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10ad4-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10ad4-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="10ad4-114">The call timed out.</span></span>|  
|<span data-ttu-id="10ad4-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10ad4-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10ad4-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="10ad4-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10ad4-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10ad4-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10ad4-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="10ad4-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10ad4-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10ad4-119">E_FAIL</span></span>|<span data-ttu-id="10ad4-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="10ad4-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10ad4-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="10ad4-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10ad4-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="10ad4-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10ad4-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10ad4-123">Remarks</span></span>  

 <span data-ttu-id="10ad4-124">`RevertToSelf` , [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) metoduna daha önceki bir çağrıdan sonra özgün iş parçacığı belirtecine dönmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="10ad4-124">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10ad4-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10ad4-125">Requirements</span></span>  

 <span data-ttu-id="10ad4-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10ad4-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10ad4-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="10ad4-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10ad4-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="10ad4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10ad4-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10ad4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ad4-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10ad4-130">See also</span></span>

- [<span data-ttu-id="10ad4-131">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10ad4-131">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="10ad4-132">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10ad4-132">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="10ad4-133">ImpersonateLoggedOnUser Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10ad4-133">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)

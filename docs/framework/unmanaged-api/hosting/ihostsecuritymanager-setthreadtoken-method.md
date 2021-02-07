---
description: ': IHostSecurityManager:: SetThreadToken yöntemi hakkında daha fazla bilgi edinin'
title: IHostSecurityManager::SetThreadToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: 96fb8d487cecc0e62d9b7787c686c74898d99d70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671405"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="9db39-103">IHostSecurityManager::SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9db39-103">IHostSecurityManager::SetThreadToken Method</span></span>

<span data-ttu-id="9db39-104">Yürütülmekte olan iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9db39-104">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db39-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9db39-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9db39-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9db39-106">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="9db39-107">'ndaki Şu anda yürütülmekte olan iş parçacığı için ayarlanacak belirtecin tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="9db39-107">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9db39-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9db39-108">Return Value</span></span>  
  
|<span data-ttu-id="9db39-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9db39-109">HRESULT</span></span>|<span data-ttu-id="9db39-110">Description</span><span class="sxs-lookup"><span data-stu-id="9db39-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9db39-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9db39-111">S_OK</span></span>|<span data-ttu-id="9db39-112">`SetThreadToken` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9db39-112">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="9db39-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9db39-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9db39-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9db39-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9db39-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9db39-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9db39-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9db39-116">The call timed out.</span></span>|  
|<span data-ttu-id="9db39-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9db39-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9db39-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9db39-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9db39-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9db39-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9db39-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9db39-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9db39-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9db39-121">E_FAIL</span></span>|<span data-ttu-id="9db39-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9db39-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9db39-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9db39-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9db39-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9db39-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9db39-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9db39-125">Remarks</span></span>  

 <span data-ttu-id="9db39-126">`IHostSecurityManager::SetThreadToken` aynı ada sahip karşılık gelen Win32 işlevine benzer şekilde davranır, Win32 işlevi çağıranın rastgele bir iş parçacığına bir tutamacı geçmesine izin verir, ancak `IHostSecurityManager::SetThreadToken` bir belirteci yalnızca şu anda yürütülmekte olan iş parçacığıyla ilişkilendirebilirler.</span><span class="sxs-lookup"><span data-stu-id="9db39-126">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="9db39-127">`HANDLE`Tür com uyumlu değildir; diğer bir deyişle, boyutu bir işletim sistemine özeldir ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9db39-127">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="9db39-128">Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ile ana bilgisayar arasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9db39-128">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db39-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9db39-129">Requirements</span></span>  

 <span data-ttu-id="9db39-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9db39-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9db39-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9db39-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9db39-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9db39-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9db39-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9db39-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db39-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9db39-134">See also</span></span>

- [<span data-ttu-id="9db39-135">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9db39-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="9db39-136">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9db39-136">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)

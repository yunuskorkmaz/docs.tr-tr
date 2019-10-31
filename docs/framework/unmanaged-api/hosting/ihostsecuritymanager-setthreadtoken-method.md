---
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
ms.openlocfilehash: aa17f637ef71373697db5ce66e4a6540c5cc5fbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139486"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="c8fcf-102">IHostSecurityManager::SetThreadToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8fcf-102">IHostSecurityManager::SetThreadToken Method</span></span>
<span data-ttu-id="c8fcf-103">Yürütülmekte olan iş parçacığı için bir tanıtıcı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8fcf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8fcf-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8fcf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8fcf-105">Parameters</span></span>  
 `hToken`  
 <span data-ttu-id="c8fcf-106">'ndaki Şu anda yürütülmekte olan iş parçacığı için ayarlanacak belirtecin tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8fcf-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c8fcf-107">Return Value</span></span>  
  
|<span data-ttu-id="c8fcf-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c8fcf-108">HRESULT</span></span>|<span data-ttu-id="c8fcf-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8fcf-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c8fcf-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c8fcf-110">S_OK</span></span>|<span data-ttu-id="c8fcf-111">`SetThreadToken` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="c8fcf-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c8fcf-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c8fcf-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c8fcf-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c8fcf-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c8fcf-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-115">The call timed out.</span></span>|  
|<span data-ttu-id="c8fcf-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c8fcf-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c8fcf-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c8fcf-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c8fcf-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c8fcf-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c8fcf-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="c8fcf-120">E_FAIL</span></span>|<span data-ttu-id="c8fcf-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c8fcf-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c8fcf-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8fcf-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8fcf-124">Remarks</span></span>  
 <span data-ttu-id="c8fcf-125">`IHostSecurityManager::SetThreadToken`, aynı ada sahip karşılık gelen Win32 işlevine benzer şekilde davranır, ancak `IHostSecurityManager::SetThreadToken`, bir belirteci yalnızca yürütülmekte olan iş parçacığıyla ilişkilendirebilirler.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="c8fcf-126">`HANDLE` türü COM uyumlu değil; diğer bir deyişle, boyutu bir işletim sistemine özeldir ve özel sıralama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="c8fcf-127">Bu nedenle, bu belirteç yalnızca işlem içinde, CLR ile ana bilgisayar arasında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8fcf-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8fcf-128">Requirements</span></span>  
 <span data-ttu-id="c8fcf-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8fcf-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8fcf-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c8fcf-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8fcf-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c8fcf-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8fcf-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8fcf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fcf-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8fcf-133">See also</span></span>

- [<span data-ttu-id="c8fcf-134">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8fcf-134">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [<span data-ttu-id="c8fcf-135">IHostThreadPoolManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8fcf-135">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)

---
title: IHostSecurityContext::Capture Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0f6ae812b64080a2c4d236a2be02ad81c4a11b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193310"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="c7b94-102">IHostSecurityContext::Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7b94-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="c7b94-103">Bir kopyasını alır [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) örnek geri çağrısından [Ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="c7b94-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7b94-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7b94-104">Syntax</span></span>  
  
```  
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7b94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7b94-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="c7b94-106">[out] Bir kopyasını adresini bir işaretçiye `IHostSecurityContext` Yakalanacak nesne.</span><span class="sxs-lookup"><span data-stu-id="c7b94-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7b94-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7b94-107">Return Value</span></span>  
  
|<span data-ttu-id="c7b94-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7b94-108">HRESULT</span></span>|<span data-ttu-id="c7b94-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7b94-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7b94-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7b94-110">S_OK</span></span>|`Capture` <span data-ttu-id="c7b94-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c7b94-111">returned successfully.</span></span>|  
|<span data-ttu-id="c7b94-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7b94-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7b94-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="c7b94-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7b94-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7b94-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7b94-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c7b94-115">The call timed out.</span></span>|  
|<span data-ttu-id="c7b94-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7b94-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7b94-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c7b94-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7b94-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7b94-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7b94-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="c7b94-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7b94-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7b94-120">E_FAIL</span></span>|<span data-ttu-id="c7b94-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c7b94-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7b94-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7b94-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7b94-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7b94-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7b94-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7b94-124">Remarks</span></span>  
 <span data-ttu-id="c7b94-125">Döndürülen arabirim işaretçisi `Capture` yakalanan içeriğinin bir kopya olması.</span><span class="sxs-lookup"><span data-stu-id="c7b94-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="c7b94-126">Bu bilgiler arasında bir zaman uyumsuz kod noktası taşındığında, yaşam süresi, işaretçiyi karşı çağrısının yapıldığı ayrılır.</span><span class="sxs-lookup"><span data-stu-id="c7b94-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="c7b94-127">Bu nedenle orijinal işaretçiyle serbest bırakılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7b94-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7b94-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7b94-128">Requirements</span></span>  
 <span data-ttu-id="c7b94-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7b94-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7b94-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7b94-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7b94-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c7b94-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c7b94-132">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c7b94-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c7b94-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7b94-133">See also</span></span>

- [<span data-ttu-id="c7b94-134">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7b94-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="c7b94-135">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7b94-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)

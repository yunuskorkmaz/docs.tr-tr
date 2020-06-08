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
ms.openlocfilehash: e1df31ed8b652837a33b360b1378f99e6800cbea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501527"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="fb64d-102">IHostSecurityContext::Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb64d-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="fb64d-103">[IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)çağrısından döndürülen [IHostSecurityContext](ihostsecuritycontext-interface.md) örneğinin bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="fb64d-103">Gets a clone of the [IHostSecurityContext](ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb64d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fb64d-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb64d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb64d-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="fb64d-106">dışı Yakalanacak nesnenin bir kopyasının adresine yönelik bir işaretçi `IHostSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="fb64d-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb64d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fb64d-107">Return Value</span></span>  
  
|<span data-ttu-id="fb64d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb64d-108">HRESULT</span></span>|<span data-ttu-id="fb64d-109">Description</span><span class="sxs-lookup"><span data-stu-id="fb64d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb64d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb64d-110">S_OK</span></span>|<span data-ttu-id="fb64d-111">`Capture`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fb64d-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="fb64d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb64d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb64d-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fb64d-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fb64d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fb64d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fb64d-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fb64d-115">The call timed out.</span></span>|  
|<span data-ttu-id="fb64d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fb64d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fb64d-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fb64d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fb64d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fb64d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fb64d-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fb64d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fb64d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb64d-120">E_FAIL</span></span>|<span data-ttu-id="fb64d-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fb64d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fb64d-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fb64d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fb64d-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb64d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb64d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb64d-124">Remarks</span></span>  
 <span data-ttu-id="fb64d-125">Öğesinden döndürülen arabirim işaretçisi, `Capture` yakalanan bağlamın bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="fb64d-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="fb64d-126">Bu bilgiler zaman uyumsuz bir kod noktasına taşındığında, yaşam süresi Çağrının yapıldığı işaretçiden bu yana karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="fb64d-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="fb64d-127">Bu nedenle özgün işaretçi serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="fb64d-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb64d-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb64d-128">Requirements</span></span>  
 <span data-ttu-id="fb64d-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb64d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb64d-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb64d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb64d-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fb64d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb64d-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb64d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb64d-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb64d-133">See also</span></span>

- [<span data-ttu-id="fb64d-134">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb64d-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="fb64d-135">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb64d-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)

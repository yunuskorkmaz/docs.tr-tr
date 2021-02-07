---
description: 'Şu konuda daha fazla bilgi edinin: IHostSecurityContext:: Capture yöntemi'
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
ms.openlocfilehash: d46bbae7b94dcad6d1356243c938c9d3690f26a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671717"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="a25f6-103">IHostSecurityContext::Capture Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a25f6-103">IHostSecurityContext::Capture Method</span></span>

<span data-ttu-id="a25f6-104">[IHostSecurityManager:: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md)çağrısından döndürülen [IHostSecurityContext](ihostsecuritycontext-interface.md) örneğinin bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="a25f6-104">Gets a clone of the [IHostSecurityContext](ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a25f6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a25f6-105">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a25f6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a25f6-106">Parameters</span></span>  

 `ppClonedContext`  
 <span data-ttu-id="a25f6-107">dışı Yakalanacak nesnenin bir kopyasının adresine yönelik bir işaretçi `IHostSecurityContext` .</span><span class="sxs-lookup"><span data-stu-id="a25f6-107">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a25f6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a25f6-108">Return Value</span></span>  
  
|<span data-ttu-id="a25f6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a25f6-109">HRESULT</span></span>|<span data-ttu-id="a25f6-110">Description</span><span class="sxs-lookup"><span data-stu-id="a25f6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a25f6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a25f6-111">S_OK</span></span>|<span data-ttu-id="a25f6-112">`Capture` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a25f6-112">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="a25f6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a25f6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a25f6-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a25f6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a25f6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a25f6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a25f6-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a25f6-116">The call timed out.</span></span>|  
|<span data-ttu-id="a25f6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a25f6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a25f6-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a25f6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a25f6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a25f6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a25f6-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a25f6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a25f6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a25f6-121">E_FAIL</span></span>|<span data-ttu-id="a25f6-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a25f6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a25f6-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a25f6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a25f6-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a25f6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a25f6-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a25f6-125">Remarks</span></span>  

 <span data-ttu-id="a25f6-126">Öğesinden döndürülen arabirim işaretçisi, `Capture` yakalanan bağlamın bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="a25f6-126">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="a25f6-127">Bu bilgiler zaman uyumsuz bir kod noktasına taşındığında, yaşam süresi Çağrının yapıldığı işaretçiden bu yana karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a25f6-127">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="a25f6-128">Bu nedenle özgün işaretçi serbest bırakılır.</span><span class="sxs-lookup"><span data-stu-id="a25f6-128">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a25f6-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a25f6-129">Requirements</span></span>  

 <span data-ttu-id="a25f6-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a25f6-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a25f6-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a25f6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a25f6-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a25f6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a25f6-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a25f6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a25f6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a25f6-134">See also</span></span>

- [<span data-ttu-id="a25f6-135">IHostSecurityContext Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a25f6-135">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="a25f6-136">IHostSecurityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a25f6-136">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)

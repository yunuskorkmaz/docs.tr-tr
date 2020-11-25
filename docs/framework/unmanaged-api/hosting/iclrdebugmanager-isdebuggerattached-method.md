---
title: ICLRDebugManager::IsDebuggerAttached Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: 71e11d7db3bd679e7972fb2f6ce098edc3399885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731026"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="eda0a-102">ICLRDebugManager::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eda0a-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>

<span data-ttu-id="eda0a-103">Bir hata ayıklayıcının işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="eda0a-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda0a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="eda0a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eda0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eda0a-105">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="eda0a-106">[out] `true` bir hata ayıklayıcısı işleme eklenmişse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="eda0a-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eda0a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eda0a-107">Return Value</span></span>  
  
|<span data-ttu-id="eda0a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eda0a-108">HRESULT</span></span>|<span data-ttu-id="eda0a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eda0a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eda0a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eda0a-110">S_OK</span></span>|<span data-ttu-id="eda0a-111">`IsDebuggerAttached` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="eda0a-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="eda0a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eda0a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eda0a-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="eda0a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eda0a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eda0a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eda0a-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="eda0a-115">The call timed out.</span></span>|  
|<span data-ttu-id="eda0a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eda0a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eda0a-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="eda0a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eda0a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eda0a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eda0a-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="eda0a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eda0a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eda0a-120">E_FAIL</span></span>|<span data-ttu-id="eda0a-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="eda0a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eda0a-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="eda0a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eda0a-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="eda0a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eda0a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eda0a-124">Remarks</span></span>  

 <span data-ttu-id="eda0a-125">`IsDebuggerAttached` bir hata ayıklayıcının işleme eklenip eklenmeyeceğini anlamak için konağın CLR 'yi sorgulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="eda0a-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda0a-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eda0a-126">Requirements</span></span>  

 <span data-ttu-id="eda0a-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eda0a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eda0a-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="eda0a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eda0a-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="eda0a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eda0a-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eda0a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda0a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eda0a-131">See also</span></span>

- [<span data-ttu-id="eda0a-132">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eda0a-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="eda0a-133">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eda0a-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="eda0a-134">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eda0a-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)

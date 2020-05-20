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
ms.openlocfilehash: a21391f52a27e7f7a3abe533499c6b2581ec4a73
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615764"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="57c47-102">ICLRDebugManager::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57c47-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="57c47-103">Bir hata ayıklayıcının işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="57c47-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c47-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="57c47-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57c47-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57c47-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="57c47-106">[out] `true` bir hata ayıklayıcısı işleme eklenmişse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="57c47-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57c47-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57c47-107">Return Value</span></span>  
  
|<span data-ttu-id="57c47-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57c47-108">HRESULT</span></span>|<span data-ttu-id="57c47-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57c47-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57c47-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57c47-110">S_OK</span></span>|<span data-ttu-id="57c47-111">`IsDebuggerAttached`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="57c47-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="57c47-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57c47-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57c47-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="57c47-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57c47-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57c47-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57c47-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="57c47-115">The call timed out.</span></span>|  
|<span data-ttu-id="57c47-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57c47-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57c47-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="57c47-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57c47-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57c47-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57c47-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="57c47-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57c47-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57c47-120">E_FAIL</span></span>|<span data-ttu-id="57c47-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="57c47-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57c47-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="57c47-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57c47-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="57c47-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57c47-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57c47-124">Remarks</span></span>  
 <span data-ttu-id="57c47-125">`IsDebuggerAttached`bir hata ayıklayıcının işleme eklenip eklenmeyeceğini anlamak için konağın CLR 'yi sorgulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="57c47-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c47-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57c47-126">Requirements</span></span>  
 <span data-ttu-id="57c47-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57c47-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c47-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57c47-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57c47-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="57c47-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57c47-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57c47-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c47-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57c47-131">See also</span></span>

- [<span data-ttu-id="57c47-132">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c47-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="57c47-133">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c47-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="57c47-134">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57c47-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)

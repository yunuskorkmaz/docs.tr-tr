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
ms.openlocfilehash: a58fcb6c1fa2aad96cdd29194a21eaf590536cdd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129388"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="16fa5-102">ICLRDebugManager::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16fa5-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="16fa5-103">Bir hata ayıklayıcının işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="16fa5-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16fa5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16fa5-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16fa5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16fa5-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="16fa5-106">[out] işleme bir hata ayıklayıcı ekli ise `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="16fa5-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16fa5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="16fa5-107">Return Value</span></span>  
  
|<span data-ttu-id="16fa5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16fa5-108">HRESULT</span></span>|<span data-ttu-id="16fa5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16fa5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16fa5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="16fa5-110">S_OK</span></span>|<span data-ttu-id="16fa5-111">`IsDebuggerAttached` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="16fa5-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="16fa5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="16fa5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="16fa5-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="16fa5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="16fa5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="16fa5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="16fa5-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="16fa5-115">The call timed out.</span></span>|  
|<span data-ttu-id="16fa5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="16fa5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="16fa5-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="16fa5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="16fa5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="16fa5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="16fa5-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="16fa5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="16fa5-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="16fa5-120">E_FAIL</span></span>|<span data-ttu-id="16fa5-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="16fa5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="16fa5-122">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16fa5-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="16fa5-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="16fa5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16fa5-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16fa5-124">Remarks</span></span>  
 <span data-ttu-id="16fa5-125">`IsDebuggerAttached`, ana bilgisayarın bir hata ayıklayıcının işleme eklenip eklenmeyeceğini belirlemede CLR 'yi sorgulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="16fa5-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16fa5-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16fa5-126">Requirements</span></span>  
 <span data-ttu-id="16fa5-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16fa5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16fa5-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="16fa5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16fa5-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="16fa5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16fa5-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16fa5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16fa5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16fa5-131">See also</span></span>

- [<span data-ttu-id="16fa5-132">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16fa5-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="16fa5-133">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16fa5-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="16fa5-134">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16fa5-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

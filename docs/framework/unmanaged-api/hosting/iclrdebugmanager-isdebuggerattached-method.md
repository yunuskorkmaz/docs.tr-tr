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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa085d9883f2a94a623f7800278c74a88e6a69a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432914"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="7128a-102">ICLRDebugManager::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7128a-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="7128a-103">İşleme bir hata ayıklayıcısı ekli olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="7128a-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7128a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7128a-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7128a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7128a-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="7128a-106">[out] `true` bir hata ayıklayıcısı ekli işlemine; Aksi takdirde ise `false`.</span><span class="sxs-lookup"><span data-stu-id="7128a-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7128a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7128a-107">Return Value</span></span>  
  
|<span data-ttu-id="7128a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7128a-108">HRESULT</span></span>|<span data-ttu-id="7128a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7128a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7128a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7128a-110">S_OK</span></span>|<span data-ttu-id="7128a-111">`IsDebuggerAttached` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7128a-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="7128a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7128a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7128a-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7128a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7128a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7128a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7128a-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7128a-115">The call timed out.</span></span>|  
|<span data-ttu-id="7128a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7128a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7128a-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="7128a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7128a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7128a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7128a-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="7128a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7128a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7128a-120">E_FAIL</span></span>|<span data-ttu-id="7128a-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7128a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7128a-122">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7128a-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7128a-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7128a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7128a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7128a-124">Remarks</span></span>  
 <span data-ttu-id="7128a-125">`IsDebuggerAttached` işleme bir hata ayıklayıcısı ekli olup olmadığını belirlemek için CLR sorgulamak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="7128a-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7128a-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7128a-126">Requirements</span></span>  
 <span data-ttu-id="7128a-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7128a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7128a-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7128a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7128a-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7128a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7128a-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7128a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7128a-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7128a-131">See Also</span></span>  
 [<span data-ttu-id="7128a-132">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7128a-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="7128a-133">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7128a-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="7128a-134">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7128a-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

---
title: ICLRTaskManager::SetUILocale Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: 051bd5cb846eb4e6e3390e17b3011a1c5b50bc45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127872"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="5d8e8-102">ICLRTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d8e8-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="5d8e8-103">Ana bilgisayarın şu anda yürütülmekte olan görevde Kullanıcı arabirimi (UI) yerel ayarını veya kültürü değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d8e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d8e8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d8e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d8e8-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="5d8e8-106">'ndaki Kullanıcı arabirimi için yeni atanan coğrafi kültür ve dil ile eşleşen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d8e8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d8e8-107">Return Value</span></span>  
  
|<span data-ttu-id="5d8e8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d8e8-108">HRESULT</span></span>|<span data-ttu-id="5d8e8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d8e8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d8e8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d8e8-110">S_OK</span></span>|<span data-ttu-id="5d8e8-111">`SetUILocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="5d8e8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d8e8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d8e8-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d8e8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d8e8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d8e8-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-115">The call timed out.</span></span>|  
|<span data-ttu-id="5d8e8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d8e8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d8e8-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d8e8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d8e8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d8e8-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d8e8-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="5d8e8-120">E_FAIL</span></span>|<span data-ttu-id="5d8e8-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d8e8-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d8e8-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d8e8-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d8e8-124">Remarks</span></span>  
 <span data-ttu-id="5d8e8-125">`SetUILocale`, ana bilgisayarın yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d8e8-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d8e8-126">Requirements</span></span>  
 <span data-ttu-id="5d8e8-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d8e8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d8e8-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5d8e8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d8e8-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5d8e8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d8e8-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d8e8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d8e8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d8e8-131">See also</span></span>

- [<span data-ttu-id="5d8e8-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d8e8-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5d8e8-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d8e8-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5d8e8-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d8e8-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5d8e8-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d8e8-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)

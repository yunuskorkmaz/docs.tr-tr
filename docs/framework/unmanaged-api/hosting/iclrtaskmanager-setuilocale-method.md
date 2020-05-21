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
ms.openlocfilehash: e6ab7c7af1cf9f30f6708c4e970db619ca071343
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762788"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="4b98d-102">ICLRTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b98d-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="4b98d-103">Ana bilgisayarın şu anda yürütülmekte olan görevde Kullanıcı arabirimi (UI) yerel ayarını veya kültürü değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="4b98d-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b98d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4b98d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b98d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b98d-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="4b98d-106">'ndaki Kullanıcı arabirimi için yeni atanan coğrafi kültür ve dil ile eşleşen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="4b98d-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b98d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4b98d-107">Return Value</span></span>  
  
|<span data-ttu-id="4b98d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b98d-108">HRESULT</span></span>|<span data-ttu-id="4b98d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b98d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b98d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b98d-110">S_OK</span></span>|<span data-ttu-id="4b98d-111">`SetUILocale`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4b98d-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="4b98d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4b98d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4b98d-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4b98d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4b98d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4b98d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4b98d-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4b98d-115">The call timed out.</span></span>|  
|<span data-ttu-id="4b98d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b98d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4b98d-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4b98d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4b98d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4b98d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4b98d-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4b98d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4b98d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b98d-120">E_FAIL</span></span>|<span data-ttu-id="4b98d-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4b98d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b98d-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4b98d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4b98d-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b98d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b98d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b98d-124">Remarks</span></span>  
 <span data-ttu-id="4b98d-125">`SetUILocale`Ana bilgisayarın, yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b98d-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b98d-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b98d-126">Requirements</span></span>  
 <span data-ttu-id="4b98d-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b98d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b98d-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4b98d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b98d-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="4b98d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b98d-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b98d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b98d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b98d-131">See also</span></span>

- [<span data-ttu-id="4b98d-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b98d-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4b98d-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b98d-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4b98d-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b98d-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4b98d-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b98d-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

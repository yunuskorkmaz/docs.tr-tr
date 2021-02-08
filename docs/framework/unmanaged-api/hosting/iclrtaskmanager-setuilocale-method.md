---
description: ': ICLRTaskManager:: Setuıcale yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f4fcc916c520489bd1e39f6a44bc1bb971df4bba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799466"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="a891a-103">ICLRTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a891a-103">ICLRTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="a891a-104">Ana bilgisayarın şu anda yürütülmekte olan görevde Kullanıcı arabirimi (UI) yerel ayarını veya kültürü değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="a891a-104">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a891a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a891a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a891a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a891a-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="a891a-107">'ndaki Kullanıcı arabirimi için yeni atanan coğrafi kültür ve dil ile eşleşen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="a891a-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a891a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a891a-108">Return Value</span></span>  
  
|<span data-ttu-id="a891a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a891a-109">HRESULT</span></span>|<span data-ttu-id="a891a-110">Description</span><span class="sxs-lookup"><span data-stu-id="a891a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a891a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a891a-111">S_OK</span></span>|<span data-ttu-id="a891a-112">`SetUILocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a891a-112">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="a891a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a891a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a891a-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a891a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a891a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a891a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a891a-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a891a-116">The call timed out.</span></span>|  
|<span data-ttu-id="a891a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a891a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a891a-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a891a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a891a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a891a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a891a-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a891a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a891a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a891a-121">E_FAIL</span></span>|<span data-ttu-id="a891a-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a891a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a891a-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a891a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a891a-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a891a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a891a-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a891a-125">Remarks</span></span>  

 <span data-ttu-id="a891a-126">`SetUILocale` Ana bilgisayarın, yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="a891a-126">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a891a-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a891a-127">Requirements</span></span>  

 <span data-ttu-id="a891a-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a891a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a891a-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a891a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a891a-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a891a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a891a-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a891a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a891a-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a891a-132">See also</span></span>

- [<span data-ttu-id="a891a-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a891a-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a891a-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a891a-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a891a-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a891a-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a891a-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a891a-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

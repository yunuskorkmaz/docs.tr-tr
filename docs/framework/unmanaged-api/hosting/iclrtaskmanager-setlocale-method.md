---
description: ': ICLRTaskManager:: SetLocale Yöntemi hakkında daha fazla bilgi edinin'
title: ICLRTaskManager::SetLocale Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 401f227f900ab4b89cd6fc5b7902b4314a7687e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799487"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="779bc-103">ICLRTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="779bc-103">ICLRTaskManager::SetLocale Method</span></span>

<span data-ttu-id="779bc-104">Ana bilgisayarın şu anda yürütülmekte olan görevde yerel ayar tanımlayıcısının (coğrafi kültür ve dille eşlenir) değerini değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="779bc-104">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="779bc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="779bc-105">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="779bc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="779bc-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="779bc-107">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="779bc-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="779bc-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="779bc-108">Return Value</span></span>  
  
|<span data-ttu-id="779bc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="779bc-109">HRESULT</span></span>|<span data-ttu-id="779bc-110">Description</span><span class="sxs-lookup"><span data-stu-id="779bc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="779bc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="779bc-111">S_OK</span></span>|<span data-ttu-id="779bc-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="779bc-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="779bc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="779bc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="779bc-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="779bc-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="779bc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="779bc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="779bc-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="779bc-116">The call timed out.</span></span>|  
|<span data-ttu-id="779bc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="779bc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="779bc-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="779bc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="779bc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="779bc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="779bc-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="779bc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="779bc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="779bc-121">E_FAIL</span></span>|<span data-ttu-id="779bc-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="779bc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="779bc-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="779bc-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="779bc-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="779bc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="779bc-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="779bc-125">Remarks</span></span>  

 <span data-ttu-id="779bc-126">`SetLocale` Ana bilgisayara, yerel ayarların eşitlenmesi için sahip olabileceği mekanizmaların yürütülmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="779bc-126">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="779bc-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="779bc-127">Requirements</span></span>  

 <span data-ttu-id="779bc-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="779bc-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="779bc-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="779bc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="779bc-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="779bc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="779bc-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="779bc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="779bc-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="779bc-132">See also</span></span>

- [<span data-ttu-id="779bc-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779bc-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="779bc-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779bc-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="779bc-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779bc-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="779bc-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="779bc-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

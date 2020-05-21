---
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
ms.openlocfilehash: 8f316d91aab4c3862a0ad45b41539a4b80791ab9
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762798"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="c512a-102">ICLRTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c512a-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="c512a-103">Ana bilgisayarın şu anda yürütülmekte olan görevde yerel ayar tanımlayıcısının (coğrafi kültür ve dille eşlenir) değerini değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="c512a-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c512a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c512a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c512a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c512a-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="c512a-106">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="c512a-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c512a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c512a-107">Return Value</span></span>  
  
|<span data-ttu-id="c512a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c512a-108">HRESULT</span></span>|<span data-ttu-id="c512a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c512a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c512a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c512a-110">S_OK</span></span>|<span data-ttu-id="c512a-111">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c512a-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="c512a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c512a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c512a-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c512a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c512a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c512a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c512a-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c512a-115">The call timed out.</span></span>|  
|<span data-ttu-id="c512a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c512a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c512a-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c512a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c512a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c512a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c512a-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c512a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c512a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c512a-120">E_FAIL</span></span>|<span data-ttu-id="c512a-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c512a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c512a-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c512a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c512a-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c512a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c512a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c512a-124">Remarks</span></span>  
 <span data-ttu-id="c512a-125">`SetLocale`Ana bilgisayara, yerel ayarların eşitlenmesi için sahip olabileceği mekanizmaların yürütülmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="c512a-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c512a-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c512a-126">Requirements</span></span>  
 <span data-ttu-id="c512a-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c512a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c512a-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c512a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c512a-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c512a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c512a-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c512a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c512a-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c512a-131">See also</span></span>

- [<span data-ttu-id="c512a-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c512a-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="c512a-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c512a-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="c512a-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c512a-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="c512a-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c512a-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)

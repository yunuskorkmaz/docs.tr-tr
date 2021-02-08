---
description: ': IHostTaskManager:: Setuıcale yöntemi hakkında daha fazla bilgi edinin'
title: IHostTaskManager::SetUILocale Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: 0b81f127c6afb64670424a05db6cc57c4918396a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789391"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="19361-103">IHostTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19361-103">IHostTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="19361-104">Ana bilgisayara, ortak dil çalışma zamanının (CLR) Şu anda yürütülmekte olan görevde Kullanıcı arabirimi (UI) yerel ayarını veya kültürü değiştirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="19361-104">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19361-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19361-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19361-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19361-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="19361-107">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="19361-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19361-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="19361-108">Return Value</span></span>  
  
|<span data-ttu-id="19361-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19361-109">HRESULT</span></span>|<span data-ttu-id="19361-110">Description</span><span class="sxs-lookup"><span data-stu-id="19361-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19361-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="19361-111">S_OK</span></span>|<span data-ttu-id="19361-112">`SetUILocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="19361-112">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="19361-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19361-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19361-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="19361-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19361-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19361-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19361-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="19361-116">The call timed out.</span></span>|  
|<span data-ttu-id="19361-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19361-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19361-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="19361-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19361-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19361-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19361-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="19361-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19361-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19361-121">E_FAIL</span></span>|<span data-ttu-id="19361-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="19361-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19361-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="19361-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19361-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="19361-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="19361-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="19361-125">E_NOTIMPL</span></span>|<span data-ttu-id="19361-126">Konak, yönetilen kullanıcı kodunun UI kültürünü değiştirmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="19361-126">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19361-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19361-127">Remarks</span></span>  

 <span data-ttu-id="19361-128">Çalışma zamanı, `SetUILocale` <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliğin değeri yönetilen kod tarafından değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="19361-128">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="19361-129">Bu yöntem, ana bilgisayarın yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="19361-129">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="19361-130">Bir konak, Kullanıcı arabirimi yerel ayarının yönetilen koddan değiştirilmesine izin vermez veya yerel ayarları eşitlemeye yönelik bir mekanizma uygulamaz, bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="19361-130">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19361-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19361-131">Requirements</span></span>  

 <span data-ttu-id="19361-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19361-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19361-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19361-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19361-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="19361-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19361-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19361-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19361-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19361-136">See also</span></span>

- [<span data-ttu-id="19361-137">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19361-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="19361-138">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19361-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="19361-139">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19361-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="19361-140">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19361-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="19361-141">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19361-141">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)

---
description: ': IHostTaskManager:: SetLocale Yöntemi hakkında daha fazla bilgi edinin'
title: IHostTaskManager::SetLocale Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 522a3da9bcd8d61754684091f6de3f11f7ed478c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789417"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="0cfce-103">IHostTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cfce-103">IHostTaskManager::SetLocale Method</span></span>

<span data-ttu-id="0cfce-104">Ana bilgisayara, ortak dil çalışma zamanının (CLR) Şu anda yürütülmekte olan görevde yerel ayarı veya kültürü değiştirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="0cfce-104">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cfce-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cfce-105">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cfce-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cfce-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="0cfce-107">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="0cfce-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cfce-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0cfce-108">Return Value</span></span>  
  
|<span data-ttu-id="0cfce-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0cfce-109">HRESULT</span></span>|<span data-ttu-id="0cfce-110">Description</span><span class="sxs-lookup"><span data-stu-id="0cfce-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cfce-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0cfce-111">S_OK</span></span>|<span data-ttu-id="0cfce-112">`SetLocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0cfce-112">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="0cfce-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0cfce-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0cfce-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0cfce-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0cfce-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0cfce-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0cfce-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0cfce-116">The call timed out.</span></span>|  
|<span data-ttu-id="0cfce-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0cfce-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0cfce-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0cfce-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0cfce-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0cfce-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0cfce-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0cfce-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0cfce-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0cfce-121">E_FAIL</span></span>|<span data-ttu-id="0cfce-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0cfce-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0cfce-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0cfce-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0cfce-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cfce-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0cfce-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0cfce-125">E_NOTIMPL</span></span>|<span data-ttu-id="0cfce-126">Konak, yönetilen kullanıcı kodunun yerel ayarı değiştirmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0cfce-126">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cfce-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cfce-127">Remarks</span></span>  

 <span data-ttu-id="0cfce-128">Çalışma zamanı, `SetLocale` <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliğin değeri yönetilen kod tarafından değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0cfce-128">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="0cfce-129">Bu yöntem, ana bilgisayarın yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cfce-129">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="0cfce-130">Bir konak yerel ayarın yönetilen koddan değiştirilmesine izin vermezse veya yerel ayarları eşitlemeye yönelik bir mekanizma uygulamaz, bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="0cfce-130">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cfce-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cfce-131">Requirements</span></span>  

 <span data-ttu-id="0cfce-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cfce-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cfce-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0cfce-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0cfce-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0cfce-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0cfce-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cfce-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cfce-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cfce-136">See also</span></span>

- [<span data-ttu-id="0cfce-137">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cfce-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="0cfce-138">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cfce-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0cfce-139">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cfce-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0cfce-140">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cfce-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="0cfce-141">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0cfce-141">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)

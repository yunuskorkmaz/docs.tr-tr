---
description: 'Şu konuda daha fazla bilgi edinin: IHostCrst:: Enter yöntemi'
title: IHostCrst::Enter Yöntemi
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: ef8e4ce71cde75fe6b834802b08d22aedbd6fab9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789456"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="0d358-103">IHostCrst::Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d358-103">IHostCrst::Enter Method</span></span>

<span data-ttu-id="0d358-104">Geçerli [IHostCrst](ihostcrst-interface.md) örneği tarafından temsil edilen kritik bölüme girer.</span><span class="sxs-lookup"><span data-stu-id="0d358-104">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d358-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d358-105">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d358-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d358-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="0d358-107">'ndaki [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri, işlem engelliyorsa konağın yapması gereken eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d358-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d358-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0d358-108">Return Value</span></span>  
  
|<span data-ttu-id="0d358-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d358-109">HRESULT</span></span>|<span data-ttu-id="0d358-110">Description</span><span class="sxs-lookup"><span data-stu-id="0d358-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d358-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d358-111">S_OK</span></span>|<span data-ttu-id="0d358-112">`Enter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0d358-112">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="0d358-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0d358-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0d358-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0d358-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0d358-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0d358-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0d358-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0d358-116">The call timed out.</span></span>|  
|<span data-ttu-id="0d358-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0d358-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0d358-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0d358-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0d358-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0d358-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0d358-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0d358-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0d358-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0d358-121">E_FAIL</span></span>|<span data-ttu-id="0d358-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0d358-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0d358-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0d358-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0d358-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d358-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d358-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d358-125">Remarks</span></span>  

 <span data-ttu-id="0d358-126">`Enter` Win32 işlevini yansıtır `EnterCriticalSection` .</span><span class="sxs-lookup"><span data-stu-id="0d358-126">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d358-127">Bu yöntem, kritik bölüm girilene kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="0d358-127">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d358-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d358-128">Requirements</span></span>  

 <span data-ttu-id="0d358-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d358-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d358-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0d358-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d358-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="0d358-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d358-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d358-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d358-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d358-133">See also</span></span>

- [<span data-ttu-id="0d358-134">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d358-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="0d358-135">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d358-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="0d358-136">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d358-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)

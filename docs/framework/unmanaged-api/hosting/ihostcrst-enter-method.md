---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a472b686799bfec4b53b8880a0c52c6f0846b03a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442383"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="c37e1-102">IHostCrst::Enter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c37e1-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="c37e1-103">Geçerli tarafından temsil edilen kritik bölüm girer [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="c37e1-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c37e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c37e1-104">Syntax</span></span>  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c37e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c37e1-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="c37e1-106">[in] Aşağıdakilerden birini [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) değerleri, ana bilgisayar varsa almalıdır hangi eylemini belirten işlemi engeller.</span><span class="sxs-lookup"><span data-stu-id="c37e1-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c37e1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c37e1-107">Return Value</span></span>  
  
|<span data-ttu-id="c37e1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c37e1-108">HRESULT</span></span>|<span data-ttu-id="c37e1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c37e1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c37e1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c37e1-110">S_OK</span></span>|<span data-ttu-id="c37e1-111">`Enter` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c37e1-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="c37e1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c37e1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c37e1-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c37e1-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c37e1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c37e1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c37e1-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c37e1-115">The call timed out.</span></span>|  
|<span data-ttu-id="c37e1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c37e1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c37e1-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="c37e1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c37e1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c37e1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c37e1-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="c37e1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c37e1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c37e1-120">E_FAIL</span></span>|<span data-ttu-id="c37e1-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c37e1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c37e1-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c37e1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c37e1-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c37e1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c37e1-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c37e1-124">Remarks</span></span>  
 <span data-ttu-id="c37e1-125">`Enter` Win32 yansıtan `EnterCriticalSection` işlevi.</span><span class="sxs-lookup"><span data-stu-id="c37e1-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c37e1-126">Kritik bölüm girilene kadar bu yöntem döndürmez.</span><span class="sxs-lookup"><span data-stu-id="c37e1-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c37e1-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c37e1-127">Requirements</span></span>  
 <span data-ttu-id="c37e1-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c37e1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c37e1-129">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c37e1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c37e1-130">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c37e1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c37e1-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c37e1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c37e1-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c37e1-132">See Also</span></span>  
 [<span data-ttu-id="c37e1-133">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c37e1-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="c37e1-134">IHostCrst Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c37e1-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="c37e1-135">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c37e1-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)

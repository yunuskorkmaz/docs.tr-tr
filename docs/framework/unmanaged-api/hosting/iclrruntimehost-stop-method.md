---
title: "ICLRRuntimeHost::Stop Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3cb9eaecdec661ae56727e5fd38c7e9a3b9621d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="56b12-102">ICLRRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56b12-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="56b12-103">Kod yürütmeyi ortak dil çalışma zamanı tarafından (CLR) durdurur.</span><span class="sxs-lookup"><span data-stu-id="56b12-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56b12-104">Bu yöntem değil ana bilgisayar kaynakları serbest bırakmak, uygulama etki alanları kaldırma veya iş parçacığı yok.</span><span class="sxs-lookup"><span data-stu-id="56b12-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="56b12-105">Bu kaynakları serbest bırakmak için işlemi sonlandırmamız gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="56b12-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b12-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56b12-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="56b12-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56b12-107">Return Value</span></span>  
  
|<span data-ttu-id="56b12-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56b12-108">HRESULT</span></span>|<span data-ttu-id="56b12-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56b12-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="56b12-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="56b12-110">S_OK</span></span>|<span data-ttu-id="56b12-111">`Stop`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="56b12-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="56b12-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="56b12-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="56b12-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="56b12-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="56b12-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="56b12-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="56b12-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="56b12-115">The call timed out.</span></span>|  
|<span data-ttu-id="56b12-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="56b12-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="56b12-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="56b12-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="56b12-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="56b12-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="56b12-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="56b12-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="56b12-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="56b12-120">E_FAIL</span></span>|<span data-ttu-id="56b12-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="56b12-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="56b12-122">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="56b12-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="56b12-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="56b12-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56b12-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56b12-124">Requirements</span></span>  
 <span data-ttu-id="56b12-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56b12-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56b12-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="56b12-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="56b12-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="56b12-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56b12-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56b12-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56b12-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56b12-129">See Also</span></span>  
 [<span data-ttu-id="56b12-130">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56b12-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

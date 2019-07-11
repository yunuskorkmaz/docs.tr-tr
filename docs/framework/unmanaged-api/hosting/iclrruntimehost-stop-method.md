---
title: ICLRRuntimeHost::Stop Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97a0e6cbbd8972f58f9eedcfeb8aff1f93694064
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765663"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="a13c8-102">ICLRRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a13c8-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="a13c8-103">Ortak dil çalışma zamanı tarafından (CLR), kodun yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="a13c8-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a13c8-104">Bu yöntem değil konağa kaynakları serbest bırakmak, uygulama etki alanları kaldırma veya iş parçacığı yok.</span><span class="sxs-lookup"><span data-stu-id="a13c8-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="a13c8-105">Bu kaynakları serbest bırakmak için işlem sonlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a13c8-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a13c8-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a13c8-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a13c8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a13c8-107">Return Value</span></span>  
  
|<span data-ttu-id="a13c8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a13c8-108">HRESULT</span></span>|<span data-ttu-id="a13c8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a13c8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a13c8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a13c8-110">S_OK</span></span>|<span data-ttu-id="a13c8-111">`Stop` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a13c8-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="a13c8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a13c8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a13c8-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a13c8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a13c8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a13c8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a13c8-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a13c8-115">The call timed out.</span></span>|  
|<span data-ttu-id="a13c8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a13c8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a13c8-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a13c8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a13c8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a13c8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a13c8-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="a13c8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a13c8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a13c8-120">E_FAIL</span></span>|<span data-ttu-id="a13c8-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a13c8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a13c8-122">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a13c8-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a13c8-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a13c8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a13c8-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a13c8-124">Requirements</span></span>  
 <span data-ttu-id="a13c8-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a13c8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a13c8-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a13c8-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a13c8-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a13c8-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a13c8-128">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a13c8-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a13c8-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a13c8-129">See also</span></span>

- [<span data-ttu-id="a13c8-130">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a13c8-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

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
ms.openlocfilehash: 85116244ad21842fab025ddd48106deef75f210b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166978"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="ee312-102">ICLRRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee312-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="ee312-103">Ortak dil çalışma zamanı tarafından (CLR), kodun yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="ee312-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee312-104">Bu yöntem değil konağa kaynakları serbest bırakmak, uygulama etki alanları kaldırma veya iş parçacığı yok.</span><span class="sxs-lookup"><span data-stu-id="ee312-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="ee312-105">Bu kaynakları serbest bırakmak için işlem sonlandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee312-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee312-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ee312-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ee312-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ee312-107">Return Value</span></span>  
  
|<span data-ttu-id="ee312-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee312-108">HRESULT</span></span>|<span data-ttu-id="ee312-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee312-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ee312-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ee312-110">S_OK</span></span>|`Stop` <span data-ttu-id="ee312-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ee312-111">returned successfully.</span></span>|  
|<span data-ttu-id="ee312-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ee312-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ee312-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ee312-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ee312-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ee312-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ee312-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ee312-115">The call timed out.</span></span>|  
|<span data-ttu-id="ee312-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ee312-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ee312-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ee312-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ee312-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ee312-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ee312-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="ee312-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ee312-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ee312-120">E_FAIL</span></span>|<span data-ttu-id="ee312-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ee312-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ee312-122">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ee312-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ee312-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee312-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee312-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee312-124">Requirements</span></span>  
 <span data-ttu-id="ee312-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee312-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee312-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ee312-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ee312-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ee312-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ee312-128">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ee312-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ee312-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee312-129">See also</span></span>

- [<span data-ttu-id="ee312-130">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee312-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

---
description: ': ICLRRuntimeHost:: Stop yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3e6b1cf2aee95af6354905f6dcdcb678ff785aa6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799743"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="32861-103">ICLRRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32861-103">ICLRRuntimeHost::Stop Method</span></span>

<span data-ttu-id="32861-104">Ortak dil çalışma zamanı (CLR) tarafından kodun yürütülmesini sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="32861-104">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="32861-105">Bu yöntem, konağa kaynak yayınlamaz, uygulama etki alanlarını kaldırmaz veya iş parçacıklarını yok eder.</span><span class="sxs-lookup"><span data-stu-id="32861-105">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="32861-106">Bu kaynakları serbest bırakmak için işlemi sonlandıramalısınız.</span><span class="sxs-lookup"><span data-stu-id="32861-106">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32861-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="32861-107">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="32861-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32861-108">Return Value</span></span>  
  
|<span data-ttu-id="32861-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32861-109">HRESULT</span></span>|<span data-ttu-id="32861-110">Description</span><span class="sxs-lookup"><span data-stu-id="32861-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32861-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="32861-111">S_OK</span></span>|<span data-ttu-id="32861-112">`Stop` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="32861-112">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="32861-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32861-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32861-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="32861-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="32861-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32861-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="32861-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="32861-116">The call timed out.</span></span>|  
|<span data-ttu-id="32861-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="32861-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="32861-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="32861-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="32861-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="32861-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="32861-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="32861-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="32861-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32861-121">E_FAIL</span></span>|<span data-ttu-id="32861-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="32861-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="32861-123">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="32861-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="32861-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="32861-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="32861-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32861-125">Requirements</span></span>  

 <span data-ttu-id="32861-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32861-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32861-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="32861-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32861-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="32861-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32861-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32861-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32861-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32861-130">See also</span></span>

- [<span data-ttu-id="32861-131">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32861-131">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

---
title: "ICLRRuntimeHost::Stop Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3798c4fc451b78257373c0ac47a5e7e7c27dd048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="d52ce-102">ICLRRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d52ce-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="d52ce-103">Kod yürütmeyi ortak dil çalışma zamanı tarafından (CLR) durdurur.</span><span class="sxs-lookup"><span data-stu-id="d52ce-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d52ce-104">Bu yöntem değil ana bilgisayar kaynakları serbest bırakmak, uygulama etki alanları kaldırma veya iş parçacığı yok.</span><span class="sxs-lookup"><span data-stu-id="d52ce-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="d52ce-105">Bu kaynakları serbest bırakmak için işlemi sonlandırmamız gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="d52ce-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d52ce-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d52ce-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d52ce-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d52ce-107">Return Value</span></span>  
  
|<span data-ttu-id="d52ce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d52ce-108">HRESULT</span></span>|<span data-ttu-id="d52ce-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d52ce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d52ce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d52ce-110">S_OK</span></span>|<span data-ttu-id="d52ce-111">`Stop`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d52ce-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="d52ce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d52ce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d52ce-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d52ce-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d52ce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d52ce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d52ce-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d52ce-115">The call timed out.</span></span>|  
|<span data-ttu-id="d52ce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d52ce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d52ce-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="d52ce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d52ce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d52ce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d52ce-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="d52ce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d52ce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d52ce-120">E_FAIL</span></span>|<span data-ttu-id="d52ce-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d52ce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d52ce-122">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d52ce-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d52ce-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d52ce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d52ce-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d52ce-124">Requirements</span></span>  
 <span data-ttu-id="d52ce-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d52ce-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d52ce-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d52ce-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d52ce-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d52ce-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d52ce-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d52ce-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d52ce-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d52ce-129">See Also</span></span>  
 [<span data-ttu-id="d52ce-130">Iclrruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="d52ce-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

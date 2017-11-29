---
title: "ICorRuntimeHost::Stop Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f6bf66065293107efae7f401a584b7342f29125
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="5f9cf-102">ICorRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f9cf-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="5f9cf-103">Geçerli işlem için çalışma zamanında kod yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f9cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f9cf-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5f9cf-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5f9cf-105">Return Value</span></span>  
  
|<span data-ttu-id="5f9cf-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f9cf-106">HRESULT</span></span>|<span data-ttu-id="5f9cf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5f9cf-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f9cf-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f9cf-108">S_OK</span></span>|<span data-ttu-id="5f9cf-109">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-109">The operation was successful.</span></span>|  
|<span data-ttu-id="5f9cf-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5f9cf-110">S_FALSE</span></span>|<span data-ttu-id="5f9cf-111">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5f9cf-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5f9cf-112">E_FAIL</span></span>|<span data-ttu-id="5f9cf-113">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5f9cf-114">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5f9cf-115">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5f9cf-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5f9cf-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5f9cf-117">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f9cf-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f9cf-118">Remarks</span></span>  
 <span data-ttu-id="5f9cf-119">Çağrılacak genellikle gereksizdir `Stop` yöntemi olduğundan işlem çıktığında yürütülen kod durdurur.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f9cf-120">Çağrı sonra `Stop`, CLR aynı işlemine yeniden olamaz.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f9cf-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f9cf-121">Requirements</span></span>  
 <span data-ttu-id="5f9cf-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f9cf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f9cf-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f9cf-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f9cf-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="5f9cf-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f9cf-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="5f9cf-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9cf-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f9cf-126">See Also</span></span>  
 [<span data-ttu-id="5f9cf-127">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f9cf-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

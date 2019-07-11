---
title: ICorRuntimeHost::Stop Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1af01559e65bd80fc62cb2eba44bf21d4fa3113
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770903"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="f89de-102">ICorRuntimeHost::Stop Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f89de-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="f89de-103">Geçerli işlem için çalışma zamanında kod yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="f89de-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f89de-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f89de-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f89de-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f89de-105">Return Value</span></span>  
  
|<span data-ttu-id="f89de-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f89de-106">HRESULT</span></span>|<span data-ttu-id="f89de-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f89de-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f89de-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f89de-108">S_OK</span></span>|<span data-ttu-id="f89de-109">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="f89de-109">The operation was successful.</span></span>|  
|<span data-ttu-id="f89de-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f89de-110">S_FALSE</span></span>|<span data-ttu-id="f89de-111">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="f89de-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="f89de-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f89de-112">E_FAIL</span></span>|<span data-ttu-id="f89de-113">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f89de-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="f89de-114">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f89de-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="f89de-115">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f89de-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f89de-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f89de-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f89de-117">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f89de-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f89de-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f89de-118">Remarks</span></span>  
 <span data-ttu-id="f89de-119">Çağırmak genellikle gereksizdir `Stop` yöntemi olduğundan işlem çıktığında yürütülen kod durdurur.</span><span class="sxs-lookup"><span data-stu-id="f89de-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f89de-120">Çağrısı yapıldıktan sonra `Stop`, CLR'nin aynı işlemde yeniden kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f89de-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f89de-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f89de-121">Requirements</span></span>  
 <span data-ttu-id="f89de-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f89de-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f89de-123">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f89de-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f89de-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f89de-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f89de-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="f89de-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f89de-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f89de-126">See also</span></span>

- [<span data-ttu-id="f89de-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f89de-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

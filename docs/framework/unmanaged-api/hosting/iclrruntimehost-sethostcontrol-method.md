---
title: ICLRRuntimeHost::SetHostControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: 68b06a2840de277bdaed1dc9ce0b51e6b363c897
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120461"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="1a1c2-102">ICLRRuntimeHost::SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a1c2-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="1a1c2-103">Ortak dil çalışma zamanının (CLR), ana bilgisayarın [IHostControl arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)uygulamasını almak için kullanabileceği arabirim işaretçisini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a1c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a1c2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a1c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a1c2-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="1a1c2-106">'ndaki Konağın [IHostControl arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)uygulamasına yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a1c2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a1c2-107">Return Value</span></span>  
  
|<span data-ttu-id="1a1c2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a1c2-108">HRESULT</span></span>|<span data-ttu-id="1a1c2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a1c2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a1c2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a1c2-110">S_OK</span></span>|<span data-ttu-id="1a1c2-111">`SetHostControl` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="1a1c2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a1c2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a1c2-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1a1c2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1a1c2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1a1c2-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-115">The call timed out.</span></span>|  
|<span data-ttu-id="1a1c2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1a1c2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1a1c2-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1a1c2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1a1c2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1a1c2-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1a1c2-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="1a1c2-120">E_FAIL</span></span>|<span data-ttu-id="1a1c2-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1a1c2-122">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1a1c2-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1a1c2-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="1a1c2-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="1a1c2-125">CLR zaten başlatılmış.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a1c2-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1a1c2-126">Remarks</span></span>  
 <span data-ttu-id="1a1c2-127">CLR başlatılmadan önce `SetHostControl` çağırmanız gerekir, diğer bir deyişle, [başlatma yöntemini](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) çağırmadan veya [meta veri arabirimlerinden](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)hiçbirini kullanmadan önce.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="1a1c2-128">[CorBindToCurrentRuntime işlevini](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) veya [CorBindToRuntimeEx işlevini](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)çağırdıktan hemen sonra `SetHostControl` çağırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a1c2-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a1c2-129">Requirements</span></span>  
 <span data-ttu-id="1a1c2-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a1c2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a1c2-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1a1c2-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a1c2-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1a1c2-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a1c2-133">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a1c2-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1c2-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a1c2-134">See also</span></span>

- [<span data-ttu-id="1a1c2-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a1c2-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="1a1c2-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a1c2-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

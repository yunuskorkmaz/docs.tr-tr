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
ms.openlocfilehash: 8d6a4e1ca934c748352b0c4f5120536a4dd24e0b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703961"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="46da3-102">ICLRRuntimeHost::SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46da3-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="46da3-103">Ortak dil çalışma zamanının (CLR), ana bilgisayarın [IHostControl arabirimi](ihostcontrol-interface.md)uygulamasını almak için kullanabileceği arabirim işaretçisini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="46da3-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46da3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="46da3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46da3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46da3-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="46da3-106">'ndaki Konağın [IHostControl arabirimi](ihostcontrol-interface.md)uygulamasına yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="46da3-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46da3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="46da3-107">Return Value</span></span>  
  
|<span data-ttu-id="46da3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="46da3-108">HRESULT</span></span>|<span data-ttu-id="46da3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46da3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46da3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="46da3-110">S_OK</span></span>|<span data-ttu-id="46da3-111">`SetHostControl`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="46da3-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="46da3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="46da3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="46da3-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="46da3-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="46da3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="46da3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="46da3-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="46da3-115">The call timed out.</span></span>|  
|<span data-ttu-id="46da3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="46da3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="46da3-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="46da3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="46da3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="46da3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="46da3-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="46da3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="46da3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="46da3-120">E_FAIL</span></span>|<span data-ttu-id="46da3-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="46da3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="46da3-122">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="46da3-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="46da3-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="46da3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="46da3-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="46da3-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="46da3-125">CLR zaten başlatılmış.</span><span class="sxs-lookup"><span data-stu-id="46da3-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46da3-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46da3-126">Remarks</span></span>  
 <span data-ttu-id="46da3-127">`SetHostControl`Clr başlatılmadan önce, diğer bir deyişle, [başlangıç yöntemini](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) çağırmadan veya [meta veri arabirimlerinden](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)herhangi birini kullanmadan önce ' i çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46da3-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="46da3-128">`SetHostControl` [CorBindToCurrentRuntime Işlevini](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) veya [CorBindToRuntimeEx işlevini](corbindtoruntimeex-function.md)çağırdıktan hemen sonra çağırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="46da3-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46da3-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46da3-129">Requirements</span></span>  
 <span data-ttu-id="46da3-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46da3-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46da3-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="46da3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="46da3-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="46da3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="46da3-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46da3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46da3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46da3-134">See also</span></span>

- [<span data-ttu-id="46da3-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46da3-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="46da3-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46da3-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)

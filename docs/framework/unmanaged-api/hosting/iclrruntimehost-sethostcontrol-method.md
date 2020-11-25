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
ms.openlocfilehash: 32483be43d4d4fe9d185c091e15a13c6feb95600
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728829"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="bd9fd-102">ICLRRuntimeHost::SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bd9fd-102">ICLRRuntimeHost::SetHostControl Method</span></span>

<span data-ttu-id="bd9fd-103">Ortak dil çalışma zamanının (CLR), ana bilgisayarın [IHostControl arabirimi](ihostcontrol-interface.md)uygulamasını almak için kullanabileceği arabirim işaretçisini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd9fd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bd9fd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd9fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd9fd-105">Parameters</span></span>  

 `pHostControl`  
 <span data-ttu-id="bd9fd-106">'ndaki Konağın [IHostControl arabirimi](ihostcontrol-interface.md)uygulamasına yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd9fd-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bd9fd-107">Return Value</span></span>  
  
|<span data-ttu-id="bd9fd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd9fd-108">HRESULT</span></span>|<span data-ttu-id="bd9fd-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd9fd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd9fd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd9fd-110">S_OK</span></span>|<span data-ttu-id="bd9fd-111">`SetHostControl` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="bd9fd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd9fd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bd9fd-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bd9fd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bd9fd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bd9fd-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-115">The call timed out.</span></span>|  
|<span data-ttu-id="bd9fd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bd9fd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bd9fd-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bd9fd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bd9fd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bd9fd-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bd9fd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd9fd-120">E_FAIL</span></span>|<span data-ttu-id="bd9fd-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bd9fd-122">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bd9fd-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bd9fd-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="bd9fd-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="bd9fd-125">CLR zaten başlatılmış.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd9fd-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd9fd-126">Remarks</span></span>  

 <span data-ttu-id="bd9fd-127">`SetHostControl`Clr başlatılmadan önce, diğer bir deyişle, [başlangıç yöntemini](iclrruntimehost-start-method.md) çağırmadan veya [meta veri arabirimlerinden](../metadata/metadata-interfaces.md)herhangi birini kullanmadan önce ' i çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="bd9fd-128">`SetHostControl` [CorBindToCurrentRuntime Işlevini](corbindtocurrentruntime-function.md) veya [CorBindToRuntimeEx işlevini](corbindtoruntimeex-function.md)çağırdıktan hemen sonra çağırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd9fd-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd9fd-129">Requirements</span></span>  

 <span data-ttu-id="bd9fd-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd9fd-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd9fd-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bd9fd-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd9fd-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bd9fd-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd9fd-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd9fd-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd9fd-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd9fd-134">See also</span></span>

- [<span data-ttu-id="bd9fd-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd9fd-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="bd9fd-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd9fd-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)

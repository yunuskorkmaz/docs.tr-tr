---
title: ICLRRuntimeHost::UnloadAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
ms.openlocfilehash: cc5d0d65d213d952c0897a72d8ec38ea6b8b22db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700671"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="2481e-102">ICLRRuntimeHost::UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2481e-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>

<span data-ttu-id="2481e-103"><xref:System.AppDomain>Belirtilen sayısal tanımlayıcıya karşılık gelen yönetilen öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2481e-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2481e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2481e-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2481e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2481e-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="2481e-106">'ndaki Boşaltılacak uygulama etki alanının sayısal tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2481e-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="2481e-107">[in] `true` ortak dil çalışma zamanının (CLR), uygulama etki alanını kaldırmayı denemeden önce uygulamanın geçerli iş parçacığını yürütmeyi bitirene kadar beklemesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="2481e-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2481e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2481e-108">Return Value</span></span>  
  
|<span data-ttu-id="2481e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2481e-109">HRESULT</span></span>|<span data-ttu-id="2481e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2481e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2481e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2481e-111">S_OK</span></span>|<span data-ttu-id="2481e-112">`UnloadAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2481e-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="2481e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2481e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2481e-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2481e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2481e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2481e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2481e-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2481e-116">The call timed out.</span></span>|  
|<span data-ttu-id="2481e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2481e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2481e-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2481e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2481e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2481e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2481e-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2481e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2481e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2481e-121">E_FAIL</span></span>|<span data-ttu-id="2481e-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2481e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2481e-123">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2481e-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2481e-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2481e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2481e-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2481e-125">Remarks</span></span>  

 <span data-ttu-id="2481e-126">[GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, geçerli iş parçacığının yürütüldüğü uygulama etki alanının sayısal tanımlayıcısını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2481e-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="2481e-127">Bu tanımlayıcı, <xref:System.AppDomain.Id%2A> yönetilen türün özelliğine karşılık gelir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="2481e-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2481e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2481e-128">Requirements</span></span>  

 <span data-ttu-id="2481e-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2481e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2481e-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2481e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2481e-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2481e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2481e-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2481e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2481e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2481e-133">See also</span></span>

- [<span data-ttu-id="2481e-134">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2481e-134">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

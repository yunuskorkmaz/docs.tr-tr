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
ms.openlocfilehash: 2a6dc878f156d5d18970fed72c9722bab60f9ba8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120402"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="38efd-102">ICLRRuntimeHost::UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38efd-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="38efd-103">Belirtilen sayısal tanımlayıcıya karşılık gelen yönetilen <xref:System.AppDomain> kaldırır.</span><span class="sxs-lookup"><span data-stu-id="38efd-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38efd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38efd-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38efd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38efd-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="38efd-106">'ndaki Boşaltılacak uygulama etki alanının sayısal tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="38efd-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="38efd-107">[in] ortak dil çalışma zamanının (CLR), uygulama etki alanını kaldırmayı denemeden önce uygulamanın geçerli iş parçacığını yürütmeyi bitirene kadar beklemesi gerektiğini belirtmek için `true`.</span><span class="sxs-lookup"><span data-stu-id="38efd-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38efd-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="38efd-108">Return Value</span></span>  
  
|<span data-ttu-id="38efd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38efd-109">HRESULT</span></span>|<span data-ttu-id="38efd-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38efd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38efd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="38efd-111">S_OK</span></span>|<span data-ttu-id="38efd-112">`UnloadAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="38efd-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="38efd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38efd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38efd-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="38efd-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38efd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38efd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38efd-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="38efd-116">The call timed out.</span></span>|  
|<span data-ttu-id="38efd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38efd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38efd-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="38efd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38efd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38efd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38efd-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="38efd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38efd-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="38efd-121">E_FAIL</span></span>|<span data-ttu-id="38efd-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="38efd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38efd-123">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="38efd-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38efd-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="38efd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38efd-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38efd-125">Remarks</span></span>  
 <span data-ttu-id="38efd-126">[GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, geçerli iş parçacığının yürütüldüğü uygulama etki alanının sayısal tanımlayıcısını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38efd-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="38efd-127">Bu tanımlayıcı, yönetilen <xref:System.AppDomain> türünün <xref:System.AppDomain.Id%2A> özelliğine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="38efd-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38efd-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38efd-128">Requirements</span></span>  
 <span data-ttu-id="38efd-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38efd-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38efd-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38efd-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38efd-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="38efd-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38efd-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38efd-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38efd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38efd-133">See also</span></span>

- [<span data-ttu-id="38efd-134">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38efd-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

---
description: ': ICLRRuntimeHost:: UnloadAppDomain yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2a47c6250434c3ee4122f8eeae75f25ee4c08a34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637293"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="e0c48-103">ICLRRuntimeHost::UnloadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0c48-103">ICLRRuntimeHost::UnloadAppDomain Method</span></span>

<span data-ttu-id="e0c48-104"><xref:System.AppDomain>Belirtilen sayısal tanımlayıcıya karşılık gelen yönetilen öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e0c48-104">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0c48-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0c48-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0c48-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e0c48-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="e0c48-107">'ndaki Boşaltılacak uygulama etki alanının sayısal tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="e0c48-107">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="e0c48-108">[in] `true` ortak dil çalışma zamanının (CLR), uygulama etki alanını kaldırmayı denemeden önce uygulamanın geçerli iş parçacığını yürütmeyi bitirene kadar beklemesi gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="e0c48-108">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0c48-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e0c48-109">Return Value</span></span>  
  
|<span data-ttu-id="e0c48-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0c48-110">HRESULT</span></span>|<span data-ttu-id="e0c48-111">Description</span><span class="sxs-lookup"><span data-stu-id="e0c48-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0c48-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0c48-112">S_OK</span></span>|<span data-ttu-id="e0c48-113">`UnloadAppDomain` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e0c48-113">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="e0c48-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0c48-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0c48-115">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e0c48-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e0c48-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e0c48-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e0c48-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e0c48-117">The call timed out.</span></span>|  
|<span data-ttu-id="e0c48-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e0c48-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e0c48-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e0c48-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e0c48-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e0c48-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e0c48-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e0c48-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e0c48-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0c48-122">E_FAIL</span></span>|<span data-ttu-id="e0c48-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e0c48-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e0c48-124">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e0c48-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e0c48-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e0c48-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0c48-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0c48-126">Remarks</span></span>  

 <span data-ttu-id="e0c48-127">[GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md)çağırarak, geçerli iş parçacığının yürütüldüğü uygulama etki alanının sayısal tanımlayıcısını alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0c48-127">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="e0c48-128">Bu tanımlayıcı, <xref:System.AppDomain.Id%2A> yönetilen türün özelliğine karşılık gelir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="e0c48-128">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0c48-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0c48-129">Requirements</span></span>  

 <span data-ttu-id="e0c48-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0c48-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0c48-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e0c48-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0c48-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e0c48-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0c48-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0c48-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c48-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0c48-134">See also</span></span>

- [<span data-ttu-id="e0c48-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0c48-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

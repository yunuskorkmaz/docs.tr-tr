---
title: ICLRControl::SetAppDomainManagerType Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: e62f9fd6b8421ea131eff0e6b36523718589c921
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615838"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="2d173-102">ICLRControl::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d173-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="2d173-103"><xref:System.AppDomainManager>Uygulama etki alanı yöneticileri için tür olarak türetilmiş bir tür belirler.</span><span class="sxs-lookup"><span data-stu-id="2d173-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d173-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2d173-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d173-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d173-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="2d173-106">'ndaki İstenen türün içinden türetildiği derlemenin adı <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="2d173-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="2d173-107">'ndaki `pwzAppDomainManagerAssembly`Özelliklerini uygulayan parametresinde uygulanan türün adı <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="2d173-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d173-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d173-108">Return Value</span></span>  
  
|<span data-ttu-id="2d173-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d173-109">HRESULT</span></span>|<span data-ttu-id="2d173-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d173-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d173-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d173-111">S_OK</span></span>|<span data-ttu-id="2d173-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2d173-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="2d173-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d173-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d173-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2d173-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d173-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d173-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d173-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2d173-116">The call timed out.</span></span>|  
|<span data-ttu-id="2d173-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d173-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d173-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2d173-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d173-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d173-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d173-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2d173-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d173-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d173-121">E_FAIL</span></span>|<span data-ttu-id="2d173-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2d173-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d173-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2d173-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d173-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d173-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2d173-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d173-125">Requirements</span></span>  
 <span data-ttu-id="2d173-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d173-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d173-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2d173-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d173-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2d173-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d173-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d173-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d173-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d173-130">See also</span></span>

- [<span data-ttu-id="2d173-131">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d173-131">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="2d173-132">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d173-132">IHostControl Interface</span></span>](ihostcontrol-interface.md)

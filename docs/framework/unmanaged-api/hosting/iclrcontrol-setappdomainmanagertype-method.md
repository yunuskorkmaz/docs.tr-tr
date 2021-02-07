---
description: ': ICLRControl:: SetAppDomainManagerType yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 20d45a0ab14904c778a6ea821fcd63f85b6b0921
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716672"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="01f94-103">ICLRControl::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01f94-103">ICLRControl::SetAppDomainManagerType Method</span></span>

<span data-ttu-id="01f94-104"><xref:System.AppDomainManager>Uygulama etki alanı yöneticileri için tür olarak türetilmiş bir tür belirler.</span><span class="sxs-lookup"><span data-stu-id="01f94-104">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f94-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01f94-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f94-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01f94-106">Parameters</span></span>  

 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="01f94-107">'ndaki İstenen türün içinden türetildiği derlemenin adı <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="01f94-107">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="01f94-108">'ndaki `pwzAppDomainManagerAssembly` Özelliklerini uygulayan parametresinde uygulanan türün adı <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="01f94-108">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01f94-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="01f94-109">Return Value</span></span>  
  
|<span data-ttu-id="01f94-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01f94-110">HRESULT</span></span>|<span data-ttu-id="01f94-111">Description</span><span class="sxs-lookup"><span data-stu-id="01f94-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01f94-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="01f94-112">S_OK</span></span>|<span data-ttu-id="01f94-113">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="01f94-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="01f94-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01f94-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01f94-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="01f94-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01f94-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01f94-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01f94-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="01f94-117">The call timed out.</span></span>|  
|<span data-ttu-id="01f94-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01f94-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01f94-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="01f94-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01f94-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01f94-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01f94-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="01f94-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01f94-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01f94-122">E_FAIL</span></span>|<span data-ttu-id="01f94-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="01f94-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01f94-124">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="01f94-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01f94-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="01f94-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01f94-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01f94-126">Requirements</span></span>  

 <span data-ttu-id="01f94-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01f94-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f94-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01f94-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01f94-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="01f94-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01f94-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f94-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f94-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01f94-131">See also</span></span>

- [<span data-ttu-id="01f94-132">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01f94-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="01f94-133">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01f94-133">IHostControl Interface</span></span>](ihostcontrol-interface.md)

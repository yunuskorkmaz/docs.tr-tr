---
title: IHostControl::SetAppDomainManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: de264135450190fd028eb8cf12017d94cc65ffac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134718"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="7d8fb-102">IHostControl::SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d8fb-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="7d8fb-103">Ana bilgisayara bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d8fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d8fb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d8fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7d8fb-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="7d8fb-106">'ndaki Seçili <xref:System.AppDomain>sayısal tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="7d8fb-107">'ndaki Ana bilgisayarın `IUnknown`olarak uyguladığı <xref:System.AppDomainManager> nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d8fb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7d8fb-108">Return Value</span></span>  
  
|<span data-ttu-id="7d8fb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d8fb-109">HRESULT</span></span>|<span data-ttu-id="7d8fb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d8fb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d8fb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d8fb-111">S_OK</span></span>|<span data-ttu-id="7d8fb-112">`SetAppDomainManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="7d8fb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d8fb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d8fb-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d8fb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d8fb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d8fb-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-116">The call timed out.</span></span>|  
|<span data-ttu-id="7d8fb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d8fb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d8fb-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d8fb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d8fb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d8fb-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d8fb-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="7d8fb-121">E_FAIL</span></span>|<span data-ttu-id="7d8fb-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d8fb-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d8fb-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d8fb-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d8fb-125">Remarks</span></span>  
 <span data-ttu-id="7d8fb-126"><xref:System.AppDomainManager>, ana bilgisayara, yönetilen koda önyükleme yapmak ve her bir <xref:System.AppDomain>oluşturulmasını ve ayarlarını denetlemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="7d8fb-127"><xref:System.AppDomainManager>, <xref:System.AppDomain> oluşturulduğunda her <xref:System.AppDomain> yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="7d8fb-128">Seçerse, CLR, `pUnkAppDomainManager` parametresinin değerini ayarlayarak ana bilgisayara uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="7d8fb-129">`SetAppDomainManager` yöntemi uygulamasında ana bilgisayar, uygulama etki alanı Yöneticisi için derleme adını ve türünü ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d8fb-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d8fb-130">Requirements</span></span>  
 <span data-ttu-id="7d8fb-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d8fb-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d8fb-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7d8fb-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d8fb-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7d8fb-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d8fb-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d8fb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d8fb-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d8fb-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="7d8fb-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d8fb-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)

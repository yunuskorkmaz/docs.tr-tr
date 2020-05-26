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
ms.openlocfilehash: 74ffc5c92402808ae566d7cb014d9d920c384ae8
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804944"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="1f719-102">IHostControl::SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f719-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="1f719-103">Ana bilgisayara bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1f719-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f719-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1f719-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f719-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f719-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="1f719-106">'ndaki Seçili öğesinin sayısal tanımlayıcısı <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="1f719-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="1f719-107">'ndaki <xref:System.AppDomainManager>Konağın uyguladığı nesneye yönelik bir işaretçi `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="1f719-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f719-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f719-108">Return Value</span></span>  
  
|<span data-ttu-id="1f719-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f719-109">HRESULT</span></span>|<span data-ttu-id="1f719-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f719-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f719-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f719-111">S_OK</span></span>|<span data-ttu-id="1f719-112">`SetAppDomainManager`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1f719-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="1f719-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f719-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f719-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1f719-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f719-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f719-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f719-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1f719-116">The call timed out.</span></span>|  
|<span data-ttu-id="1f719-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f719-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f719-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1f719-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f719-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f719-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f719-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1f719-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f719-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f719-121">E_FAIL</span></span>|<span data-ttu-id="1f719-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1f719-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f719-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1f719-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f719-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f719-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f719-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f719-125">Remarks</span></span>  
 <span data-ttu-id="1f719-126">, <xref:System.AppDomainManager> Ana bilgisayarı yönetilen koda önyükleme yapmak ve her birinin oluşturma ve ayarlarını denetlemek için bir mekanizmaya sahip sağlar <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="1f719-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="1f719-127">, <xref:System.AppDomainManager> Oluşturulduğunda her birine yüklenir <xref:System.AppDomain> <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="1f719-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="1f719-128">Seçerse, CLR, parametrenin değerini ayarlayarak ana bilgisayara uygulama etki alanının oluşturulduğunu bildirir `pUnkAppDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="1f719-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="1f719-129">`SetAppDomainManager`Yöntemi, uygulama etki alanı yöneticisinin derleme adını ve türünü ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1f719-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f719-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f719-130">Requirements</span></span>  
 <span data-ttu-id="1f719-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f719-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f719-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1f719-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f719-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1f719-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f719-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f719-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f719-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f719-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="1f719-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f719-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)

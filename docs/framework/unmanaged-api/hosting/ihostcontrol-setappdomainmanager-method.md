---
description: ': IHostControl:: SetAppDomainManager yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1fc5efc0afad73d1805338140f186a50913ca542
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708908"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="c6e6a-103">IHostControl::SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c6e6a-103">IHostControl::SetAppDomainManager Method</span></span>

<span data-ttu-id="c6e6a-104">Ana bilgisayara bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-104">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e6a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6e6a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6e6a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c6e6a-106">Parameters</span></span>  

 `dwAppDomainID`  
 <span data-ttu-id="c6e6a-107">'ndaki Seçili öğesinin sayısal tanımlayıcısı <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="c6e6a-107">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="c6e6a-108">'ndaki <xref:System.AppDomainManager> Konağın uyguladığı nesneye yönelik bir işaretçi `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="c6e6a-108">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6e6a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c6e6a-109">Return Value</span></span>  
  
|<span data-ttu-id="c6e6a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6e6a-110">HRESULT</span></span>|<span data-ttu-id="c6e6a-111">Description</span><span class="sxs-lookup"><span data-stu-id="c6e6a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6e6a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6e6a-112">S_OK</span></span>|<span data-ttu-id="c6e6a-113">`SetAppDomainManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-113">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="c6e6a-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6e6a-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6e6a-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6e6a-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6e6a-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6e6a-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-117">The call timed out.</span></span>|  
|<span data-ttu-id="c6e6a-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6e6a-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6e6a-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6e6a-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6e6a-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6e6a-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6e6a-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6e6a-122">E_FAIL</span></span>|<span data-ttu-id="c6e6a-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6e6a-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6e6a-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6e6a-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6e6a-126">Remarks</span></span>  

 <span data-ttu-id="c6e6a-127">, <xref:System.AppDomainManager> Ana bilgisayarı yönetilen koda önyükleme yapmak ve her birinin oluşturma ve ayarlarını denetlemek için bir mekanizmaya sahip sağlar <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="c6e6a-127">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="c6e6a-128">, <xref:System.AppDomainManager> Oluşturulduğunda her birine yüklenir <xref:System.AppDomain> <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="c6e6a-128">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="c6e6a-129">Seçerse, CLR, parametrenin değerini ayarlayarak ana bilgisayara uygulama etki alanının oluşturulduğunu bildirir `pUnkAppDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="c6e6a-129">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="c6e6a-130">`SetAppDomainManager`Yöntemi, uygulama etki alanı yöneticisinin derleme adını ve türünü ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-130">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e6a-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c6e6a-131">Requirements</span></span>  

 <span data-ttu-id="c6e6a-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6e6a-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6e6a-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c6e6a-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6e6a-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c6e6a-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6e6a-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e6a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e6a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6e6a-136">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="c6e6a-137">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c6e6a-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)

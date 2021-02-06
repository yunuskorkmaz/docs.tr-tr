---
description: ': ICLRHostProtectionManager:: SetProtectedCategories yöntemi hakkında daha fazla bilgi edinin'
title: ICLRHostProtectionManager::SetProtectedCategories Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: 9138c31ea1a2d9b7ebeaeac8ef5ef9305eabef8d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637540"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="93b82-103">ICLRHostProtectionManager::SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93b82-103">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>

<span data-ttu-id="93b82-104">Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="93b82-104">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b82-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93b82-105">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93b82-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="93b82-106">Parameters</span></span>  

 `categories`  
 <span data-ttu-id="93b82-107">'ndaki Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını önlenebileceğini belirten [EApiCategories](eapicategories-enumeration.md) değerlerinin bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="93b82-107">[in] A combination of [EApiCategories](eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93b82-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="93b82-108">Return Value</span></span>  
  
|<span data-ttu-id="93b82-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93b82-109">HRESULT</span></span>|<span data-ttu-id="93b82-110">Description</span><span class="sxs-lookup"><span data-stu-id="93b82-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93b82-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="93b82-111">S_OK</span></span>|<span data-ttu-id="93b82-112">`SetProtectedCategories` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="93b82-112">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="93b82-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93b82-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93b82-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="93b82-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="93b82-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="93b82-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="93b82-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="93b82-116">The call timed out.</span></span>|  
|<span data-ttu-id="93b82-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="93b82-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="93b82-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="93b82-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="93b82-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="93b82-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="93b82-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="93b82-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="93b82-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93b82-121">E_FAIL</span></span>|<span data-ttu-id="93b82-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="93b82-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="93b82-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="93b82-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="93b82-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="93b82-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93b82-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93b82-125">Remarks</span></span>  

 <span data-ttu-id="93b82-126">Her `EApiCategories` değer, yönetilen türlerin ve üyelerin listesini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="93b82-126">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="93b82-127">`EApiCategories`Sabit listesi ve `SetProtectedCategories` yöntemi, <xref:System.Security.Permissions.HostProtectionAttribute> tarafından tanımlanan kategorilere karşılık gelen özellikleri kullanıma sunan yönetilen türleri ve üyeleri işaretlemek için kullanılan yönetilen sınıfla doğrudan ilgilidir `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="93b82-127">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="93b82-128">Daha fazla bilgi için, bkz <xref:System.Security.Permissions.HostProtectionAttribute> <xref:System.Security.Permissions.HostProtectionResource> . ve doğrudan karşılık gelen sabit listesi `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="93b82-128">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93b82-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93b82-129">Requirements</span></span>  

 <span data-ttu-id="93b82-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93b82-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b82-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="93b82-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93b82-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="93b82-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93b82-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93b82-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b82-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93b82-134">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="93b82-135">EApiCategories Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="93b82-135">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="93b82-136">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93b82-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="93b82-137">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93b82-137">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)

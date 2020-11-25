---
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
ms.openlocfilehash: 0557a8f1c7c495950933a44cacd23ada8e84964e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730506"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="ffdc2-102">ICLRHostProtectionManager::SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ffdc2-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>

<span data-ttu-id="ffdc2-103">Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffdc2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ffdc2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffdc2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ffdc2-105">Parameters</span></span>  

 `categories`  
 <span data-ttu-id="ffdc2-106">'ndaki Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını önlenebileceğini belirten [EApiCategories](eapicategories-enumeration.md) değerlerinin bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-106">[in] A combination of [EApiCategories](eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ffdc2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ffdc2-107">Return Value</span></span>  
  
|<span data-ttu-id="ffdc2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ffdc2-108">HRESULT</span></span>|<span data-ttu-id="ffdc2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffdc2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ffdc2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ffdc2-110">S_OK</span></span>|<span data-ttu-id="ffdc2-111">`SetProtectedCategories` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="ffdc2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ffdc2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ffdc2-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ffdc2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ffdc2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ffdc2-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-115">The call timed out.</span></span>|  
|<span data-ttu-id="ffdc2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ffdc2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ffdc2-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ffdc2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ffdc2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ffdc2-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ffdc2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ffdc2-120">E_FAIL</span></span>|<span data-ttu-id="ffdc2-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ffdc2-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ffdc2-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffdc2-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ffdc2-124">Remarks</span></span>  

 <span data-ttu-id="ffdc2-125">Her `EApiCategories` değer, yönetilen türlerin ve üyelerin listesini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="ffdc2-126">`EApiCategories`Sabit listesi ve `SetProtectedCategories` yöntemi, <xref:System.Security.Permissions.HostProtectionAttribute> tarafından tanımlanan kategorilere karşılık gelen özellikleri kullanıma sunan yönetilen türleri ve üyeleri işaretlemek için kullanılan yönetilen sınıfla doğrudan ilgilidir `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="ffdc2-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="ffdc2-127">Daha fazla bilgi için, bkz <xref:System.Security.Permissions.HostProtectionAttribute> <xref:System.Security.Permissions.HostProtectionResource> . ve doğrudan karşılık gelen sabit listesi `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="ffdc2-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffdc2-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ffdc2-128">Requirements</span></span>  

 <span data-ttu-id="ffdc2-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffdc2-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffdc2-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ffdc2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffdc2-131">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ffdc2-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffdc2-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffdc2-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffdc2-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffdc2-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="ffdc2-134">EApiCategories Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ffdc2-134">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="ffdc2-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffdc2-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="ffdc2-136">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ffdc2-136">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)

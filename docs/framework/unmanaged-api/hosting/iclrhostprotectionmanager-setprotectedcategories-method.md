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
ms.openlocfilehash: e3f2429462b4454e87690d98ad9fb446574add91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141040"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="72a54-102">ICLRHostProtectionManager::SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72a54-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="72a54-103">Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="72a54-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72a54-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72a54-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72a54-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="72a54-106">'ndaki Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını önlenebileceğini belirten [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) değerlerinin bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="72a54-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72a54-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72a54-107">Return Value</span></span>  
  
|<span data-ttu-id="72a54-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72a54-108">HRESULT</span></span>|<span data-ttu-id="72a54-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72a54-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72a54-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="72a54-110">S_OK</span></span>|<span data-ttu-id="72a54-111">`SetProtectedCategories` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="72a54-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="72a54-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72a54-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72a54-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="72a54-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72a54-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72a54-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72a54-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="72a54-115">The call timed out.</span></span>|  
|<span data-ttu-id="72a54-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72a54-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72a54-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="72a54-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72a54-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72a54-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72a54-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="72a54-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72a54-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="72a54-120">E_FAIL</span></span>|<span data-ttu-id="72a54-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="72a54-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72a54-122">Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="72a54-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72a54-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="72a54-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72a54-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72a54-124">Remarks</span></span>  
 <span data-ttu-id="72a54-125">Her `EApiCategories` değeri, yönetilen türlerin ve üyelerin listesini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="72a54-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="72a54-126">`EApiCategories` numaralandırması ve `SetProtectedCategories` yöntemi, `EApiCategories`tarafından tanımlanan kategorilere karşılık gelen özellikleri kullanıma sunan yönetilen türleri ve üyeleri işaretlemek için kullanılan yönetilen <xref:System.Security.Permissions.HostProtectionAttribute> sınıfıyla doğrudan ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="72a54-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="72a54-127">Daha fazla bilgi için, `EApiCategories`doğrudan karşılık gelen <xref:System.Security.Permissions.HostProtectionAttribute> ve <xref:System.Security.Permissions.HostProtectionResource> numaralandırması ' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="72a54-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a54-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72a54-128">Requirements</span></span>  
 <span data-ttu-id="72a54-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a54-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a54-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="72a54-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72a54-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="72a54-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72a54-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a54-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a54-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72a54-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="72a54-134">EApiCategories Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="72a54-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="72a54-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72a54-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="72a54-136">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72a54-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)

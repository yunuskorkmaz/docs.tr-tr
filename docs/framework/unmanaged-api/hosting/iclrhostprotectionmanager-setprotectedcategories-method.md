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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63b6e85b6abe20e9e1f0b00648a06a31735e63c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944657"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="77103-102">ICLRHostProtectionManager::SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77103-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="77103-103">Yönetilen türler ve üyeler kategorilerini kısmen güvenilen bir kod çalıştırmasını engellenmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="77103-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77103-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77103-104">Syntax</span></span>  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77103-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77103-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="77103-106">[in] Bir birleşimi [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) Kategorilerini Yönetilen türlerin ve üyelerin kısmen güvenilen kod çalıştırılmasının engellenmesi gerektiğini belirten değerleri.</span><span class="sxs-lookup"><span data-stu-id="77103-106">[in] A combination of [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77103-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="77103-107">Return Value</span></span>  
  
|<span data-ttu-id="77103-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77103-108">HRESULT</span></span>|<span data-ttu-id="77103-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77103-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77103-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="77103-110">S_OK</span></span>|<span data-ttu-id="77103-111">`SetProtectedCategories` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="77103-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="77103-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77103-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77103-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="77103-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77103-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77103-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77103-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="77103-115">The call timed out.</span></span>|  
|<span data-ttu-id="77103-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77103-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77103-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="77103-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77103-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77103-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77103-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="77103-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77103-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77103-120">E_FAIL</span></span>|<span data-ttu-id="77103-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="77103-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77103-122">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="77103-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77103-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="77103-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77103-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77103-124">Remarks</span></span>  
 <span data-ttu-id="77103-125">Her `EApiCategories` değeri Yönetilen türlerin ve üyelerin listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="77103-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="77103-126">`EApiCategories` Numaralandırma ve `SetProtectedCategories` yöntemi doğrudan ilgili için yönetilen <xref:System.Security.Permissions.HostProtectionAttribute> yönetilen türleri ve üyeleri tarafından açıklanan kategoriler karşılık gelen özellikleri kullanıma sunan işaretlemek için kullanılan sınıfı `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="77103-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="77103-127">Daha fazla bilgi için <xref:System.Security.Permissions.HostProtectionAttribute> ve <xref:System.Security.Permissions.HostProtectionResource> doğrudan karşılık gelen numaralandırma `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="77103-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77103-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77103-128">Requirements</span></span>  
 <span data-ttu-id="77103-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77103-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77103-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77103-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77103-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="77103-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77103-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77103-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77103-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77103-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="77103-134">EApiCategories Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="77103-134">EApiCategories Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [<span data-ttu-id="77103-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77103-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="77103-136">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77103-136">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)

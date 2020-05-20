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
ms.openlocfilehash: 5cf6f942add3d090cf830e71a545b9f4d4f69f00
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703168"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a><span data-ttu-id="c4025-102">ICLRHostProtectionManager::SetProtectedCategories Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4025-102">ICLRHostProtectionManager::SetProtectedCategories Method</span></span>
<span data-ttu-id="c4025-103">Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını engelleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4025-103">Specifies which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4025-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c4025-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4025-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4025-105">Parameters</span></span>  
 `categories`  
 <span data-ttu-id="c4025-106">'ndaki Kısmen güvenilen kodda hangi yönetilen tür ve üye kategorilerinin çalıştırılmasını önlenebileceğini belirten [EApiCategories](eapicategories-enumeration.md) değerlerinin bir birleşimi.</span><span class="sxs-lookup"><span data-stu-id="c4025-106">[in] A combination of [EApiCategories](eapicategories-enumeration.md) values, indicating which categories of managed types and members should be blocked from running in partially trusted code.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4025-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c4025-107">Return Value</span></span>  
  
|<span data-ttu-id="c4025-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4025-108">HRESULT</span></span>|<span data-ttu-id="c4025-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4025-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4025-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4025-110">S_OK</span></span>|<span data-ttu-id="c4025-111">`SetProtectedCategories`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c4025-111">`SetProtectedCategories` returned successfully.</span></span>|  
|<span data-ttu-id="c4025-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4025-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4025-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c4025-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4025-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4025-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4025-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c4025-115">The call timed out.</span></span>|  
|<span data-ttu-id="c4025-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4025-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4025-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c4025-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4025-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4025-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4025-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c4025-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4025-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4025-120">E_FAIL</span></span>|<span data-ttu-id="c4025-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c4025-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4025-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c4025-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4025-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c4025-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4025-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4025-124">Remarks</span></span>  
 <span data-ttu-id="c4025-125">Her `EApiCategories` değer, yönetilen türlerin ve üyelerin listesini ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c4025-125">Each `EApiCategories` value refers to a list of managed types and members.</span></span> <span data-ttu-id="c4025-126">`EApiCategories`Sabit listesi ve `SetProtectedCategories` yöntemi, <xref:System.Security.Permissions.HostProtectionAttribute> tarafından tanımlanan kategorilere karşılık gelen özellikleri kullanıma sunan yönetilen türleri ve üyeleri işaretlemek için kullanılan yönetilen sınıfla doğrudan ilgilidir `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="c4025-126">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute> class, which is used to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span> <span data-ttu-id="c4025-127">Daha fazla bilgi için, bkz <xref:System.Security.Permissions.HostProtectionAttribute> <xref:System.Security.Permissions.HostProtectionResource> . ve doğrudan karşılık gelen sabit listesi `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="c4025-127">For more information, see <xref:System.Security.Permissions.HostProtectionAttribute> and the <xref:System.Security.Permissions.HostProtectionResource> enumeration, which directly corresponds to `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4025-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4025-128">Requirements</span></span>  
 <span data-ttu-id="c4025-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4025-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4025-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c4025-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4025-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c4025-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4025-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4025-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4025-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4025-133">See also</span></span>

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [<span data-ttu-id="c4025-134">EApiCategories Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c4025-134">EApiCategories Enumeration</span></span>](eapicategories-enumeration.md)
- [<span data-ttu-id="c4025-135">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4025-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c4025-136">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4025-136">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)

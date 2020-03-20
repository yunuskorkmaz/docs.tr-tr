---
title: IHostPolicyManager::OnDefaultAction Yöntemi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnDefaultAction
helpviewer_keywords:
- OnDefaultAction method [.NET Framework hosting]
- IHostPolicyManager::OnDefaultAction method [.NET Framework hosting]
ms.assetid: 071e73bd-4795-470f-9373-cfaef553b7f2
topic_type:
- apiref
ms.openlocfilehash: 8d987614c1a5a2c90ccb3faa11c605767ae5cfda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178016"
---
# <a name="ihostpolicymanagerondefaultaction-method"></a><span data-ttu-id="1669b-102">IHostPolicyManager::OnDefaultAction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1669b-102">IHostPolicyManager::OnDefaultAction Method</span></span>
<span data-ttu-id="1669b-103">Ortak dil çalışma zamanının (CLR) [iCLRPolicyManager'a](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) yapılan bir çağrı yla ayarlanan varsayılan eylemi yapmak üzere olduğunu ana bilgisayara iliştiricine::İş parçacığının iptaline veya <xref:System.AppDomain> boşaltın'a yanıt olarak Varsayılan Eylem yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1669b-103">Notifies the host that the common language runtime (CLR) is about to take the default action that was set by a call to the [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) method in response to a thread abort or <xref:System.AppDomain> unload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1669b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1669b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnDefaultAction (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1669b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1669b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="1669b-106">[içinde] CLR'nin yanıt verme etkinliğini gösteren [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="1669b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of event to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="1669b-107">[içinde] CLR'nin olaya yanıt olarak yaptığı eylemi gösteren [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="1669b-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action that the CLR is taking in response to the event.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1669b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1669b-108">Return Value</span></span>  
  
|<span data-ttu-id="1669b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1669b-109">HRESULT</span></span>|<span data-ttu-id="1669b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1669b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1669b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1669b-111">S_OK</span></span>|<span data-ttu-id="1669b-112">`OnDefaultAction`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1669b-112">`OnDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="1669b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1669b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1669b-114">CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1669b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="1669b-115">Başarı -yla</span><span class="sxs-lookup"><span data-stu-id="1669b-115">successfully</span></span>|  
|<span data-ttu-id="1669b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1669b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1669b-117">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="1669b-117">The call timed out.</span></span>|  
|<span data-ttu-id="1669b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1669b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1669b-119">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="1669b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1669b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1669b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1669b-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1669b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1669b-122">E_faıl</span><span class="sxs-lookup"><span data-stu-id="1669b-122">E_FAIL</span></span>|<span data-ttu-id="1669b-123">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="1669b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1669b-124">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1669b-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1669b-125">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="1669b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1669b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1669b-126">Requirements</span></span>  
 <span data-ttu-id="1669b-127">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1669b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1669b-128">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1669b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1669b-129">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="1669b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1669b-130">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1669b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1669b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1669b-131">See also</span></span>

- [<span data-ttu-id="1669b-132">EClrOperation Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1669b-132">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="1669b-133">EPolicyAction Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1669b-133">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="1669b-134">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1669b-134">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="1669b-135">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1669b-135">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)

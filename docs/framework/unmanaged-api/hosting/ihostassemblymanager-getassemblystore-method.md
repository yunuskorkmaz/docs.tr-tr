---
title: IHostAssemblyManager::GetAssemblyStore Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 347947622601475147663b8838bef5f36a1f7e32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="cf3cc-102">IHostAssemblyManager::GetAssemblyStore Metodu</span><span class="sxs-lookup"><span data-stu-id="cf3cc-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="cf3cc-103">Bir arabirim işaretçisi alır bir [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) ana bilgisayar tarafından yüklenen derleme listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf3cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf3cc-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf3cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf3cc-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="cf3cc-106">[out] Bir işlev işaretçisi bir `IHostAssemblyStore` örneği veya konak uygulamazsa null `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf3cc-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cf3cc-107">Return Value</span></span>  
  
|<span data-ttu-id="cf3cc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf3cc-108">HRESULT</span></span>|<span data-ttu-id="cf3cc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf3cc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf3cc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf3cc-110">S_OK</span></span>|<span data-ttu-id="cf3cc-111">`GetAssemblyStore`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="cf3cc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cf3cc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cf3cc-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cf3cc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cf3cc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cf3cc-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-115">The call timed out.</span></span>|  
|<span data-ttu-id="cf3cc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cf3cc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cf3cc-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cf3cc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cf3cc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cf3cc-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cf3cc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf3cc-120">E_FAIL</span></span>|<span data-ttu-id="cf3cc-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cf3cc-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cf3cc-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cf3cc-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="cf3cc-124">E_NOINTERFACE</span></span>|<span data-ttu-id="cf3cc-125">Ana bilgisayar uygulaması sağlamaz `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf3cc-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf3cc-126">Remarks</span></span>  
 <span data-ttu-id="cf3cc-127">`IHostAssemblyStore`derlemeler ve modüller CLR bağımsız olarak bağlamak bir konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="cf3cc-128">Konaklar genellikle derleme depoları derlemeleri biçimlerden dosya sistemi dışında yüklenmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf3cc-129">Ana bilgisayar uygulamazsa `IHostAssemblyStore`, `GetAssemblyStore` E_NOINTERFACE HRESULT değerini döndürmelidir ve ayarlamalısınız `ppAssemblyStore` null.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf3cc-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf3cc-130">Requirements</span></span>  
 <span data-ttu-id="cf3cc-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf3cc-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf3cc-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf3cc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf3cc-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cf3cc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf3cc-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf3cc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf3cc-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf3cc-135">See Also</span></span>  
 [<span data-ttu-id="cf3cc-136">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf3cc-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="cf3cc-137">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf3cc-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

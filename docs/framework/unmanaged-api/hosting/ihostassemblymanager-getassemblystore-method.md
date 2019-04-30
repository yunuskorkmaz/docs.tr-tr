---
title: IHostAssemblyManager::GetAssemblyStore Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 35e38949ce945d93216daffd3c0d91dad6c8739b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763197"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="dea7f-102">IHostAssemblyManager::GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dea7f-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="dea7f-103">Bir arabirim işaretçisi alır bir [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) ana bilgisayar tarafından yüklenen derlemelerin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dea7f-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea7f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dea7f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dea7f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dea7f-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="dea7f-106">[out] Bir işlev işaretçisi ile bir `IHostAssemblyStore` örneği veya konak uygulamazsa, null `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="dea7f-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dea7f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dea7f-107">Return Value</span></span>  
  
|<span data-ttu-id="dea7f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dea7f-108">HRESULT</span></span>|<span data-ttu-id="dea7f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dea7f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dea7f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dea7f-110">S_OK</span></span>|<span data-ttu-id="dea7f-111">`GetAssemblyStore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="dea7f-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="dea7f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dea7f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dea7f-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="dea7f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dea7f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dea7f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dea7f-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="dea7f-115">The call timed out.</span></span>|  
|<span data-ttu-id="dea7f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dea7f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dea7f-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="dea7f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dea7f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dea7f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dea7f-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="dea7f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dea7f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dea7f-120">E_FAIL</span></span>|<span data-ttu-id="dea7f-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dea7f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dea7f-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dea7f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dea7f-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="dea7f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dea7f-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="dea7f-124">E_NOINTERFACE</span></span>|<span data-ttu-id="dea7f-125">Ana bilgisayar uygulaması sağlamaz `IHostAssemblyStore`.</span><span class="sxs-lookup"><span data-stu-id="dea7f-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dea7f-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dea7f-126">Remarks</span></span>  
 <span data-ttu-id="dea7f-127">`IHostAssemblyStore` derlemeler ve modüller CLR bağımsız olarak bağlamak konak izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dea7f-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="dea7f-128">Ana bilgisayar bütünleştirilmiş kod depoları, dosya sistemi dışında biçimlerinden yüklenecek derlemeleri izin vermek için normalde sağlar.</span><span class="sxs-lookup"><span data-stu-id="dea7f-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dea7f-129">Konak uygulamazsa `IHostAssemblyStore`, `GetAssemblyStore` e_noınterface bir HRESULT değerini döndürmelidir ve ayarlamalısınız `ppAssemblyStore` null.</span><span class="sxs-lookup"><span data-stu-id="dea7f-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dea7f-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dea7f-130">Requirements</span></span>  
 <span data-ttu-id="dea7f-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dea7f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dea7f-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dea7f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dea7f-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dea7f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dea7f-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dea7f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea7f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dea7f-135">See also</span></span>

- [<span data-ttu-id="dea7f-136">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dea7f-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="dea7f-137">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dea7f-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

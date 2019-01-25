---
title: IHostAssemblyManager::GetNonHostStoreAssemblies Metodu
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b90ddefb082b9017246bf644b79aa63c5d7444b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600186"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="2cd19-102">IHostAssemblyManager::GetNonHostStoreAssemblies Metodu</span><span class="sxs-lookup"><span data-stu-id="2cd19-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="2cd19-103">Bir arabirim işaretçisi alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) ortak dil çalışma zamanı (CLR) yüklemek için bir konak bekliyor derlemelerin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2cd19-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cd19-104">Syntax</span></span>  
  
```  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cd19-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2cd19-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="2cd19-106">[out] Adresine bir işaretçi bir `ICLRAssemblyReferenceList` konak bekliyor yüklenecek CLR derlemelerine başvurular listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2cd19-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cd19-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2cd19-107">Return Value</span></span>  
  
|<span data-ttu-id="2cd19-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2cd19-108">HRESULT</span></span>|<span data-ttu-id="2cd19-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2cd19-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2cd19-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2cd19-110">S_OK</span></span>|<span data-ttu-id="2cd19-111">`GetNonHostStoreAssemblies` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2cd19-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="2cd19-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2cd19-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2cd19-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2cd19-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2cd19-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2cd19-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2cd19-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2cd19-115">The call timed out.</span></span>|  
|<span data-ttu-id="2cd19-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2cd19-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2cd19-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="2cd19-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2cd19-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2cd19-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2cd19-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="2cd19-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2cd19-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2cd19-120">E_FAIL</span></span>|<span data-ttu-id="2cd19-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2cd19-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2cd19-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2cd19-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2cd19-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2cd19-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2cd19-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2cd19-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2cd19-125">İstenen için başvuru listesini oluşturmak yeterli bellek yoktu `ICLRAssemblyReferenceList`.</span><span class="sxs-lookup"><span data-stu-id="2cd19-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cd19-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2cd19-126">Remarks</span></span>  
 <span data-ttu-id="2cd19-127">CLR başvuruları aşağıdaki kuralları kullanarak çözer:</span><span class="sxs-lookup"><span data-stu-id="2cd19-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
-   <span data-ttu-id="2cd19-128">İlk olarak, derleme başvuruları tarafından döndürülen listesini Danışmanlığı hizmetleri `GetNonHostStoreAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="2cd19-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
-   <span data-ttu-id="2cd19-129">Derleme listesinde görünüyorsa, CLR normalde bağlar.</span><span class="sxs-lookup"><span data-stu-id="2cd19-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
-   <span data-ttu-id="2cd19-130">Derleme listesinde görünmez ve ana bilgisayar uygulaması ayarının [Ihostassemblystore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), CLR çağrıları [Ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) sağlamak konak izin vermek için bağlamak için derleme.</span><span class="sxs-lookup"><span data-stu-id="2cd19-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
-   <span data-ttu-id="2cd19-131">Aksi takdirde, CLR derlemeye bağlamak başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="2cd19-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="2cd19-132">Konak gruplarını `ppReferenceList` null olarak CLR ilk araştırmaları genel derleme önbelleği, çağıran `ProvideAssembly`ve ardından bir bütünleştirilmiş kod başvurusu çözümlemek için uygulama temel araştırmaları.</span><span class="sxs-lookup"><span data-stu-id="2cd19-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cd19-133">CLR başlatma sırasında çağırır `GetNonHostStoreAssemblies` yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="2cd19-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="2cd19-134">Yöntemi yeniden çağrılır değil.</span><span class="sxs-lookup"><span data-stu-id="2cd19-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd19-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cd19-135">Requirements</span></span>  
 <span data-ttu-id="2cd19-136">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cd19-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd19-137">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2cd19-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2cd19-138">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2cd19-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2cd19-139">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd19-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cd19-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2cd19-140">See also</span></span>
- [<span data-ttu-id="2cd19-141">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd19-141">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="2cd19-142">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd19-142">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="2cd19-143">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cd19-143">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

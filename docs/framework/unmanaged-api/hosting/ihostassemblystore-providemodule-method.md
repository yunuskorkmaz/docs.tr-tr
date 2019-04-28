---
title: IHostAssemblyStore::ProvideModule Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e07e2c3f2c6000f5a081b13316c269f322b1ef8a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599354"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="e87d8-102">IHostAssemblyStore::ProvideModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e87d8-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="e87d8-103">Modül bir derleme veya bağlı (ancak değil bir katıştırılmış) içinde kaynak dosyası çözümler.</span><span class="sxs-lookup"><span data-stu-id="e87d8-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e87d8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e87d8-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e87d8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e87d8-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="e87d8-106">[in] Bir işaretçi bir [Modulebindınfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) istenen modülün açıklayan örneği <xref:System.AppDomain>, derleme ve modül adı.</span><span class="sxs-lookup"><span data-stu-id="e87d8-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="e87d8-107">[out] Bir işaretçi için benzersiz bir tanımlayıcıya `IStream` içeren yüklenen modül.</span><span class="sxs-lookup"><span data-stu-id="e87d8-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="e87d8-108">[out] Adresine bir işaretçi bir `IStream` yüklenmesi için taşınabilir yürütülebilir (PE) görüntüsünü içeren, nesne veya modülü bulunamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="e87d8-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="e87d8-109">[out] Adresine bir işaretçi bir `IStream` nesne, istenen modülü için program hata ayıklama (PDB) bilgilerini içeren veya .pdb dosyası bulunamadı, null.</span><span class="sxs-lookup"><span data-stu-id="e87d8-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e87d8-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e87d8-110">Return Value</span></span>  
  
|<span data-ttu-id="e87d8-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e87d8-111">HRESULT</span></span>|<span data-ttu-id="e87d8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e87d8-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e87d8-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e87d8-113">S_OK</span></span>|<span data-ttu-id="e87d8-114">`ProvideModule` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e87d8-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="e87d8-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e87d8-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e87d8-116">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e87d8-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e87d8-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e87d8-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e87d8-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e87d8-118">The call timed out.</span></span>|  
|<span data-ttu-id="e87d8-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e87d8-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e87d8-120">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e87d8-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e87d8-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e87d8-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e87d8-122">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e87d8-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e87d8-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e87d8-123">E_FAIL</span></span>|<span data-ttu-id="e87d8-124">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e87d8-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e87d8-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e87d8-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e87d8-126">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e87d8-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e87d8-127">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="e87d8-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="e87d8-128">İstenen derleme veya bağlı kaynak bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="e87d8-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="e87d8-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e87d8-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e87d8-130">`pdwModuleId` döndürülecek konak istediği tanımlayıcı içerecek yeteri kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="e87d8-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e87d8-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e87d8-131">Remarks</span></span>  
 <span data-ttu-id="e87d8-132">Kimlik değeri için döndürülen `pdwModuleId` ana bilgisayar tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e87d8-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="e87d8-133">Tanımlayıcılar bir işlem yaşam süresi içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e87d8-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="e87d8-134">CLR, ilişkili akış için benzersiz tanımlayıcı olarak bu değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="e87d8-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="e87d8-135">Her değer değerlerini karşı denetler `pAssemblyId` yapılan çağrılar tarafından döndürülen [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) ve değerlerini karşı `pdwModuleId` yapılan diğer çağrılar tarafından döndürülen `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="e87d8-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="e87d8-136">Konak için başka aynı tanımlayıcı değerini döndürürse `IStream`, CLR, akış içeriğini zaten eşlendi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="e87d8-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="e87d8-137">Bu durumda, CLR görüntü yerine yeni bir eşleme var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="e87d8-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="e87d8-138">Bu nedenle, tanımlayıcı da döndürüldüğü derleme tanımlayıcıları ile örtüşmemelidir `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e87d8-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e87d8-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e87d8-139">Requirements</span></span>  
 <span data-ttu-id="e87d8-140">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e87d8-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e87d8-141">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e87d8-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e87d8-142">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e87d8-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e87d8-143">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e87d8-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e87d8-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e87d8-144">See also</span></span>

- [<span data-ttu-id="e87d8-145">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e87d8-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e87d8-146">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e87d8-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="e87d8-147">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e87d8-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

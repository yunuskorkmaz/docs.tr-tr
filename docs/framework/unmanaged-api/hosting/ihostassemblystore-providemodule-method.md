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
ms.openlocfilehash: 8b604e1d7fc3d3c8adf7d95bd95843bc0110dbc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440024"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="63959-102">IHostAssemblyStore::ProvideModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63959-102">IHostAssemblyStore::ProvideModule Method</span></span>
<span data-ttu-id="63959-103">Modül bir derlemeyi ya da bağlı (ancak olmayan bir katıştırılmış) içinde kaynak dosyası çözümler.</span><span class="sxs-lookup"><span data-stu-id="63959-103">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63959-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63959-104">Syntax</span></span>  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63959-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63959-105">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="63959-106">[in] Bir işaretçi bir [Modulebindınfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) istenen modülünün açıklar örneği <xref:System.AppDomain>, derleme ve modül adı.</span><span class="sxs-lookup"><span data-stu-id="63959-106">[in] A pointer to a [ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="63959-107">[out] İçin benzersiz bir tanımlayıcı için bir işaretçi `IStream` içeren yüklenen modül.</span><span class="sxs-lookup"><span data-stu-id="63959-107">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="63959-108">[out] Adresine bir işaretçi bir `IStream` nesnesi, yüklenecek taşınabilir yürütülebilir (PE) görüntüsünü içeren veya modül bulunamadı, boş.</span><span class="sxs-lookup"><span data-stu-id="63959-108">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="63959-109">[out] Adresine bir işaretçi bir `IStream` nesne, istenen modülünün program hata ayıklama (PDB) bilgilerini içeren veya .pdb dosyasını bulunamadı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="63959-109">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63959-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="63959-110">Return Value</span></span>  
  
|<span data-ttu-id="63959-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63959-111">HRESULT</span></span>|<span data-ttu-id="63959-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63959-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63959-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="63959-113">S_OK</span></span>|<span data-ttu-id="63959-114">`ProvideModule` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="63959-114">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="63959-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="63959-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="63959-116">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="63959-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="63959-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="63959-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="63959-118">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="63959-118">The call timed out.</span></span>|  
|<span data-ttu-id="63959-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="63959-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="63959-120">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="63959-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="63959-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="63959-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="63959-122">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="63959-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="63959-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="63959-123">E_FAIL</span></span>|<span data-ttu-id="63959-124">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="63959-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="63959-125">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="63959-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="63959-126">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="63959-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="63959-127">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="63959-127">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="63959-128">İstenen derlemeyi ya da bağlı kaynak bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="63959-128">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="63959-129">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="63959-129">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="63959-130">`pdwModuleId` döndürülecek konak istediği tanımlayıcı içerecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="63959-130">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63959-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63959-131">Remarks</span></span>  
 <span data-ttu-id="63959-132">İçin kimlik değeri döndürülen `pdwModuleId` ana bilgisayar tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="63959-132">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="63959-133">Tanımlayıcıları bir işlem yaşam süresi içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63959-133">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="63959-134">CLR ilişkili akışı için benzersiz tanımlayıcı olarak bu değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="63959-134">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="63959-135">Her değer için değerleri karşı denetler `pAssemblyId` çağrı tarafından döndürülen [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) ve değerlerini karşı `pdwModuleId` diğer çağrı tarafından döndürülen `ProvideModule`.</span><span class="sxs-lookup"><span data-stu-id="63959-135">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="63959-136">Ana bilgisayar aynı tanımlayıcısı değeri için başka bir döndürürse `IStream`, CLR, akış içeriğini zaten eşlenmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="63959-136">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="63959-137">Bu durumda, CLR var olan kopyasını yeni bir eşleme yerine görüntüsü yükler.</span><span class="sxs-lookup"><span data-stu-id="63959-137">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="63959-138">Bu nedenle, tanımlayıcı ayrıca döndürülen derleme tanımlayıcıları ile çakışmaması gerekir `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="63959-138">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63959-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63959-139">Requirements</span></span>  
 <span data-ttu-id="63959-140">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63959-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63959-141">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63959-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63959-142">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="63959-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63959-143">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63959-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63959-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63959-144">See Also</span></span>  
 [<span data-ttu-id="63959-145">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63959-145">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="63959-146">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63959-146">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="63959-147">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63959-147">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

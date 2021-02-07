---
description: 'Şu konuda daha fazla bilgi edinin: IHostAssemblyStore::P rovideModule yöntemi'
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
ms.openlocfilehash: 9e783b9f8db303d095995507689d7567225a51fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709034"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="9a699-103">IHostAssemblyStore::ProvideModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a699-103">IHostAssemblyStore::ProvideModule Method</span></span>

<span data-ttu-id="9a699-104">Derleme içindeki bir modülü veya bağlı (gömülü) bir kaynak dosyasını çözer.</span><span class="sxs-lookup"><span data-stu-id="9a699-104">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a699-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a699-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a699-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a699-106">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="9a699-107">'ndaki İstenen modülün [](modulebindinfo-structure.md) <xref:System.AppDomain> , derlemenin ve modül adının açıklandığı bir ModuleBindInfo örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9a699-107">[in] A pointer to a [ModuleBindInfo](modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="9a699-108">dışı Yüklenen modülün bulunduğu bir benzersiz tanımlayıcı işaretçisi `IStream` .</span><span class="sxs-lookup"><span data-stu-id="9a699-108">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="9a699-109">dışı `IStream` Yüklenecek Taşınabilir çalıştırılabilir (PE) görüntüsünü içeren bir nesnenin adresine yönelik bir işaretçi veya modül bulunamazsa null.</span><span class="sxs-lookup"><span data-stu-id="9a699-109">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="9a699-110">dışı `IStream` İstenen modüle yönelik program hata ayıklama (pdb) bilgilerini içeren nesnenin adresine yönelik bir işaretçi veya. pdb dosyası bulunamazsa null.</span><span class="sxs-lookup"><span data-stu-id="9a699-110">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a699-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a699-111">Return Value</span></span>  
  
|<span data-ttu-id="9a699-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a699-112">HRESULT</span></span>|<span data-ttu-id="9a699-113">Description</span><span class="sxs-lookup"><span data-stu-id="9a699-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a699-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a699-114">S_OK</span></span>|<span data-ttu-id="9a699-115">`ProvideModule` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9a699-115">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="9a699-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a699-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a699-117">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9a699-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a699-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a699-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a699-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9a699-119">The call timed out.</span></span>|  
|<span data-ttu-id="9a699-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a699-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a699-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9a699-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a699-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a699-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a699-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9a699-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a699-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a699-124">E_FAIL</span></span>|<span data-ttu-id="9a699-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9a699-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a699-126">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9a699-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a699-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a699-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a699-128">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="9a699-128">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="9a699-129">İstenen derleme veya bağlı kaynak bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="9a699-129">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="9a699-130">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9a699-130">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9a699-131">`pdwModuleId` , konağın döndürmek istediği tanımlayıcıyı içerecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="9a699-131">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a699-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a699-132">Remarks</span></span>  

 <span data-ttu-id="9a699-133">İçin döndürülen kimlik değeri `pdwModuleId` ana bilgisayar tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9a699-133">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="9a699-134">Tanımlayıcılar bir işlemin ömrü içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9a699-134">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="9a699-135">CLR bu değeri ilişkili akış için benzersiz tanımlayıcı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a699-135">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="9a699-136">Her bir değeri `pAssemblyId` , [ProvideAssembly](ihostassemblystore-provideassembly-method.md) çağrıları tarafından döndürülen değerlere ve `pdwModuleId` diğer çağrıları tarafından döndürülen değerlere karşı denetler `ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="9a699-136">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="9a699-137">Konak diğeri için aynı tanımlayıcı değerini döndürürse `IStream` , clr bu akışın içeriğinin zaten eşlenmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="9a699-137">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="9a699-138">Bu durumda, CLR yeni bir tane eşlemek yerine görüntünün var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="9a699-138">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="9a699-139">Bu nedenle, tanımlayıcı aynı zamanda öğesinden döndürülen derleme tanımlayıcılarıyla çakışmamalıdır `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="9a699-139">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a699-140">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a699-140">Requirements</span></span>  

 <span data-ttu-id="9a699-141">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a699-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a699-142">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9a699-142">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a699-143">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9a699-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a699-144">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a699-144">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a699-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a699-145">See also</span></span>

- [<span data-ttu-id="9a699-146">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a699-146">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9a699-147">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a699-147">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="9a699-148">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a699-148">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)

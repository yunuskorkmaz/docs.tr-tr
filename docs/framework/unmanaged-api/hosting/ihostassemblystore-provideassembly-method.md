---
description: 'Şu konuda daha fazla bilgi edinin: IHostAssemblyStore::P rovideAssembly yöntemi'
title: IHostAssemblyStore::ProvideAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
ms.openlocfilehash: f8917cb28dd3898343a7b6ee08bd54096df8cfa7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789508"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="61750-103">IHostAssemblyStore::ProvideAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="61750-103">IHostAssemblyStore::ProvideAssembly Method</span></span>

<span data-ttu-id="61750-104">[IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)öğesinden döndürülen [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) tarafından başvurulmayan bir derlemeye başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="61750-104">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="61750-105">Ortak dil çalışma zamanı (CLR), `ProvideAssembly` Listede görünmeyen her derleme için çağırır.</span><span class="sxs-lookup"><span data-stu-id="61750-105">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61750-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61750-106">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61750-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61750-107">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="61750-108">'ndaki Herhangi bir sürüm oluşturma ilkesinin varlığı veya yokluğu ve hangi derlemenin bağlanacağı dahil olmak üzere, konağın belirli bağlama özelliklerini belirlemede kullandığı bir [AssemblyBindInfo](assemblybindinfo-structure.md) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="61750-108">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="61750-109">dışı Bunun için istenen derleme için benzersiz bir tanımlayıcı işaretçisi `IStream` .</span><span class="sxs-lookup"><span data-stu-id="61750-109">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="61750-110">dışı Platform çağırma çağrısına gerek olmadan istenen derlemenin kanıtını belirlemede kullanılan, konağa özgü verilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="61750-110">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="61750-111">`pHostContext`<xref:System.Reflection.Assembly.HostContext%2A>yönetilen sınıfın özelliğine karşılık gelir <xref:System.Reflection.Assembly> .</span><span class="sxs-lookup"><span data-stu-id="61750-111">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="61750-112">dışı `IStream` Yüklenecek Taşınabilir çalıştırılabilir (PE) görüntüsünü içeren bir adresine yönelik bir işaretçi veya derleme bulunamazsa null.</span><span class="sxs-lookup"><span data-stu-id="61750-112">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="61750-113">dışı `IStream` Program hata ayıklama (pdb) bilgilerini içeren bir adresine yönelik bir işaretçi veya. pdb dosyası bulunamazsa null.</span><span class="sxs-lookup"><span data-stu-id="61750-113">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61750-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61750-114">Return Value</span></span>  
  
|<span data-ttu-id="61750-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61750-115">HRESULT</span></span>|<span data-ttu-id="61750-116">Description</span><span class="sxs-lookup"><span data-stu-id="61750-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61750-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="61750-117">S_OK</span></span>|<span data-ttu-id="61750-118">`ProvideAssembly` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="61750-118">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="61750-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61750-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61750-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="61750-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="61750-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="61750-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="61750-122">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="61750-122">The call timed out.</span></span>|  
|<span data-ttu-id="61750-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="61750-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="61750-124">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="61750-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="61750-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="61750-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="61750-126">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="61750-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="61750-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61750-127">E_FAIL</span></span>|<span data-ttu-id="61750-128">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="61750-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="61750-129">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="61750-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="61750-130">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="61750-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="61750-131">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="61750-131">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="61750-132">İstenen derleme bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="61750-132">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="61750-133">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="61750-133">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="61750-134">Tarafından belirtilen arabellek boyutu, `pAssemblyId` konağın döndürmek istediği tanımlayıcıyı tutabilecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="61750-134">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61750-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="61750-135">Remarks</span></span>  

 <span data-ttu-id="61750-136">İçin döndürülen kimlik değeri `pAssemblyId` ana bilgisayar tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="61750-136">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="61750-137">Tanımlayıcılar bir işlemin ömrü içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="61750-137">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="61750-138">CLR bu değeri akış için benzersiz bir tanımlayıcı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="61750-138">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="61750-139">Her değeri, `pAssemblyId` için diğer çağrılar tarafından döndürülen değerlere karşı denetler `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="61750-139">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="61750-140">Konak `pAssemblyId` diğeri için aynı değeri döndürürse `IStream` , clr bu akışın içeriğinin zaten eşlenmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="61750-140">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="61750-141">Öyleyse, çalışma zamanı yeni bir tane eşlemek yerine görüntünün var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="61750-141">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61750-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61750-142">Requirements</span></span>  

 <span data-ttu-id="61750-143">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61750-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61750-144">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="61750-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61750-145">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="61750-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61750-146">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61750-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61750-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61750-147">See also</span></span>

- [<span data-ttu-id="61750-148">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61750-148">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="61750-149">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61750-149">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="61750-150">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61750-150">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)

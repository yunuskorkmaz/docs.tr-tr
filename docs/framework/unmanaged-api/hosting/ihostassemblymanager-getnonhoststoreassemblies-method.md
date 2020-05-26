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
ms.openlocfilehash: 0dc2f625da7f4e37583f198c8d6dba86f6dcdb10
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805062"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="0ca89-102">IHostAssemblyManager::GetNonHostStoreAssemblies Metodu</span><span class="sxs-lookup"><span data-stu-id="0ca89-102">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>
<span data-ttu-id="0ca89-103">Konağın ortak dil çalışma zamanı (CLR) yüklenmesini beklediği derlemelerin listesini temsil eden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) öğesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="0ca89-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca89-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0ca89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ca89-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ca89-105">Parameters</span></span>  
 `ppReferenceList`  
 <span data-ttu-id="0ca89-106">dışı `ICLRAssemblyReferenceList`KONAĞıN clr 'nin yüklenmesini beklediği derlemelere yönelik başvuruların listesini içeren adresinin bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0ca89-106">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ca89-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ca89-107">Return Value</span></span>  
  
|<span data-ttu-id="0ca89-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ca89-108">HRESULT</span></span>|<span data-ttu-id="0ca89-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ca89-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ca89-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ca89-110">S_OK</span></span>|<span data-ttu-id="0ca89-111">`GetNonHostStoreAssemblies`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0ca89-111">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="0ca89-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ca89-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ca89-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0ca89-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ca89-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ca89-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ca89-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0ca89-115">The call timed out.</span></span>|  
|<span data-ttu-id="0ca89-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ca89-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ca89-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0ca89-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ca89-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ca89-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ca89-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0ca89-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ca89-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ca89-120">E_FAIL</span></span>|<span data-ttu-id="0ca89-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0ca89-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ca89-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ca89-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ca89-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ca89-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ca89-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="0ca89-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="0ca89-125">İstenen için başvuruların listesini oluşturmak üzere yeterli kullanılabilir bellek yoktu `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="0ca89-125">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ca89-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ca89-126">Remarks</span></span>  
 <span data-ttu-id="0ca89-127">CLR, aşağıdaki kılavuz kümesini kullanarak başvuruları çözümler:</span><span class="sxs-lookup"><span data-stu-id="0ca89-127">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="0ca89-128">İlk olarak, tarafından döndürülen derleme başvuruları listesini inceleyerek `GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="0ca89-128">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="0ca89-129">Derleme listede görünürse, CLR buna normal olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="0ca89-129">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="0ca89-130">Derleme listede görünmezse ve konak [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)'un bir uygulamasını SAĞLADıYSA, clr 'nin bağlanacak derlemeyi sağlaması Için [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) ' ı çağırır.</span><span class="sxs-lookup"><span data-stu-id="0ca89-130">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="0ca89-131">Aksi takdirde, CLR derlemeye bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="0ca89-131">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="0ca89-132">Konak `ppReferenceList` null olarak ayarlanırsa, clr ilk olarak genel derleme önbelleğini yoklamalar, çağırır `ProvideAssembly` ve ardından derleme başvurusunu çözümlemek için uygulama temelini yoklamalar.</span><span class="sxs-lookup"><span data-stu-id="0ca89-132">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca89-133">Başlatma sonrasında CLR `GetNonHostStoreAssemblies` yalnızca bir kez çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="0ca89-133">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="0ca89-134">Yöntemi yeniden çağrılmadı.</span><span class="sxs-lookup"><span data-stu-id="0ca89-134">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ca89-135">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ca89-135">Requirements</span></span>  
 <span data-ttu-id="0ca89-136">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ca89-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca89-137">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ca89-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ca89-138">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0ca89-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ca89-139">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ca89-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca89-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ca89-140">See also</span></span>

- [<span data-ttu-id="0ca89-141">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ca89-141">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="0ca89-142">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ca89-142">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="0ca89-143">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ca89-143">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)

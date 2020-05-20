---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
ms.openlocfilehash: 98af9931e219c384b017d3c70fe21cdb6e052ac1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615962"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="c494e-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c494e-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="c494e-103">Belirtilen kimlik türüyle derleme tarafından başvurulan derleme kimlikleri için bir [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) numaralandırıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="c494e-103">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c494e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c494e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c494e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c494e-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="c494e-106">'ndaki WinNT. h içinde tanımlanan işlemci mimarisini belirten geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="c494e-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c494e-107">'ndaki Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c494e-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="c494e-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="c494e-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="c494e-109">'ndaki Genellikle [ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) veya [ICLRAssemblyIdentityManager:: GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metoduna yapılan çağrıdan döndürülen donuk bir derleme bağlama kimliği.</span><span class="sxs-lookup"><span data-stu-id="c494e-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="c494e-110">dışı `ICLRProbingAssemblyEnum`Tarafından tanımlanan derlemenin başvurduğu derlemelere yönelik başvuruları içeren bir Numaralandırıcı için arabirim işaretçisi `pwzReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="c494e-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c494e-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c494e-111">Return Value</span></span>  
  
|<span data-ttu-id="c494e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c494e-112">HRESULT</span></span>|<span data-ttu-id="c494e-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c494e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c494e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c494e-114">S_OK</span></span>|<span data-ttu-id="c494e-115">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c494e-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="c494e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c494e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c494e-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c494e-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c494e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c494e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c494e-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c494e-119">The call timed out.</span></span>|  
|<span data-ttu-id="c494e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c494e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c494e-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c494e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c494e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c494e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c494e-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c494e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c494e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c494e-124">E_FAIL</span></span>|<span data-ttu-id="c494e-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c494e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c494e-126">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c494e-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c494e-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c494e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c494e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c494e-128">Requirements</span></span>  
 <span data-ttu-id="c494e-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c494e-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c494e-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c494e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c494e-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c494e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c494e-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c494e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c494e-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c494e-133">See also</span></span>

- [<span data-ttu-id="c494e-134">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c494e-134">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="c494e-135">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c494e-135">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="c494e-136">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c494e-136">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)

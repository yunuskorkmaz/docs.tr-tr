---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9655981bf7ca21a6f59b305f6ea3fa5ff47f608a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773404"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="65c6d-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65c6d-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="65c6d-103">Bir işaretçi alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen akış derlemede tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="65c6d-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65c6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65c6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65c6d-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="65c6d-106">[in] Bir arabirim işaretçisi için bir `IStream` değerlendirilecek derlemeyi içeren.</span><span class="sxs-lookup"><span data-stu-id="65c6d-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="65c6d-107">[in] Sonra genişletilebilmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="65c6d-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="65c6d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT geçerli ortak dil çalışma zamanı (CLR) sürümünü destekleyen tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="65c6d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="65c6d-109">[in] Bir işaretçi bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) dışında tutulan derlemeler için derleme kimlik verilerini içeren nesne `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="65c6d-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="65c6d-110">[out] Adresine bir işaretçi bir `ICLRReferenceAssemblyEnum` derlemesinde tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne `pStream`, derlemeleri hariç `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="65c6d-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65c6d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="65c6d-111">Return Value</span></span>  
  
|<span data-ttu-id="65c6d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65c6d-112">HRESULT</span></span>|<span data-ttu-id="65c6d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65c6d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65c6d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="65c6d-114">S_OK</span></span>|<span data-ttu-id="65c6d-115">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="65c6d-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="65c6d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65c6d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65c6d-117">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="65c6d-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65c6d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65c6d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65c6d-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="65c6d-119">The call timed out.</span></span>|  
|<span data-ttu-id="65c6d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65c6d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65c6d-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="65c6d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65c6d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65c6d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65c6d-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="65c6d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65c6d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65c6d-124">E_FAIL</span></span>|<span data-ttu-id="65c6d-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="65c6d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65c6d-126">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="65c6d-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65c6d-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="65c6d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65c6d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65c6d-128">Remarks</span></span>  
 <span data-ttu-id="65c6d-129">Arayan, döndürülen listeden bir dizi bilinen bütünleştirilmiş kod başvuruları dışlanacak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65c6d-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="65c6d-130">Bu tarafından tanımlanan `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="65c6d-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c6d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65c6d-131">Requirements</span></span>  
 <span data-ttu-id="65c6d-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c6d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c6d-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65c6d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65c6d-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="65c6d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65c6d-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c6d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c6d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65c6d-136">See also</span></span>

- [<span data-ttu-id="65c6d-137">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65c6d-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="65c6d-138">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65c6d-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="65c6d-139">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65c6d-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)

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
ms.openlocfilehash: f4c200ad23ff7a71298e84fda857912da53978a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126691"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="38220-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38220-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="38220-103">Belirtilen akıştaki derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren bir [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) nesnesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="38220-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38220-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38220-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38220-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38220-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="38220-106">'ndaki Değerlendirilecek derlemeyi içeren `IStream` bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="38220-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="38220-107">'ndaki Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="38220-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="38220-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="38220-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="38220-109">'ndaki `ppReferenceEnum`dışında tutulacak derlemeler için derleme kimliği verilerini içeren [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38220-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="38220-110">dışı `pExcludeAssembliesList`derlemeleri hariç `pStream`derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren `ICLRReferenceAssemblyEnum` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="38220-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38220-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="38220-111">Return Value</span></span>  
  
|<span data-ttu-id="38220-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38220-112">HRESULT</span></span>|<span data-ttu-id="38220-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38220-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38220-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="38220-114">S_OK</span></span>|<span data-ttu-id="38220-115">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="38220-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="38220-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38220-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38220-117">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="38220-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38220-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38220-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38220-119">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="38220-119">The call timed out.</span></span>|  
|<span data-ttu-id="38220-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38220-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38220-121">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="38220-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38220-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38220-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38220-123">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="38220-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38220-124">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="38220-124">E_FAIL</span></span>|<span data-ttu-id="38220-125">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="38220-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38220-126">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="38220-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38220-127">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="38220-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38220-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38220-128">Remarks</span></span>  
 <span data-ttu-id="38220-129">Çağıran, bir bilinen derleme başvuruları kümesini döndürülen listeden dışlamayı tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="38220-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="38220-130">Bu küme `pExcludeAssembliesList`tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="38220-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38220-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38220-131">Requirements</span></span>  
 <span data-ttu-id="38220-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38220-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38220-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="38220-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38220-134">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="38220-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38220-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38220-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38220-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38220-136">See also</span></span>

- [<span data-ttu-id="38220-137">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38220-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="38220-138">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38220-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="38220-139">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="38220-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)

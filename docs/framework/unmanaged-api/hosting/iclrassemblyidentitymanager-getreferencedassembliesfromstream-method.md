---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64a43640d08acbab0bcf505cc8a5850784ff18ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="4a9f1-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Metodu</span><span class="sxs-lookup"><span data-stu-id="4a9f1-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>
<span data-ttu-id="4a9f1-103">Bir işaretçi alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen stream derlemede tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-103">Gets a pointer to an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a9f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a9f1-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a9f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a9f1-105">Parameters</span></span>  
 `pStream`  
 <span data-ttu-id="4a9f1-106">[in] Bir arabirim işaretçisi bir `IStream` değerlendirilecek derlemeyi içeren.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-106">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4a9f1-107">[in] Gelecekteki genişletilebilirliği için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="4a9f1-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT ortak dil çalışma zamanı (CLR) geçerli sürümünü destekleyen tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="4a9f1-109">[in] Bir işaretçi bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) dışında tutulması derlemeler için derleme kimlik verilerini içeren nesne `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="4a9f1-110">[out] Adresine bir işaretçi bir `ICLRReferenceAssemblyEnum` derlemesi tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne `pStream`, derlemelerde hariç `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a9f1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4a9f1-111">Return Value</span></span>  
  
|<span data-ttu-id="4a9f1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a9f1-112">HRESULT</span></span>|<span data-ttu-id="4a9f1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a9f1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a9f1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a9f1-114">S_OK</span></span>|<span data-ttu-id="4a9f1-115">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="4a9f1-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a9f1-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a9f1-117">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a9f1-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a9f1-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a9f1-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-119">The call timed out.</span></span>|  
|<span data-ttu-id="4a9f1-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a9f1-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a9f1-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a9f1-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a9f1-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a9f1-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a9f1-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a9f1-124">E_FAIL</span></span>|<span data-ttu-id="4a9f1-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a9f1-126">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a9f1-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a9f1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a9f1-128">Remarks</span></span>  
 <span data-ttu-id="4a9f1-129">Çağıran bir bilinen derleme başvurularını döndürülen listesinden hariç seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="4a9f1-130">Bu küme tarafından tanımlanan `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-130">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a9f1-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a9f1-131">Requirements</span></span>  
 <span data-ttu-id="4a9f1-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a9f1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a9f1-133">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a9f1-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a9f1-134">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4a9f1-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a9f1-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a9f1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a9f1-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a9f1-136">See Also</span></span>  
 [<span data-ttu-id="4a9f1-137">Iclrassemblyıdentitymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a9f1-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="4a9f1-138">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a9f1-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="4a9f1-139">Iclrreferenceassemblyenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a9f1-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)

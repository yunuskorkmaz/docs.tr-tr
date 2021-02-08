---
description: ': ICLRAssemblyIdentityManager:: GetReferencedAssembliesFromFile yöntemi hakkında daha fazla bilgi edinin'
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
ms.openlocfilehash: 46b2f392746c6e23e2a8a11aded5eacd8f5a597b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790067"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="e4b46-103">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4b46-103">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>

<span data-ttu-id="e4b46-104">Belirtilen dosya yolundaki derleme tarafından başvurulan derlemelerin listesini içeren bir [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="e4b46-104">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b46-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4b46-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4b46-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4b46-106">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="e4b46-107">'ndaki Değerlendirilecek derlemenin yolu.</span><span class="sxs-lookup"><span data-stu-id="e4b46-107">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e4b46-108">'ndaki Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e4b46-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="e4b46-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="e4b46-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="e4b46-110">'ndaki İçinden dışlanmalıdır derlemeleri temsil eden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) nesnesine yönelik bir işaretçi `ppReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="e4b46-110">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="e4b46-111">dışı `ICLRReferenceAssemblyEnum` `pwzFilePath` Tarafından temsil edilen derlemeler hariç olmak üzere derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren bir nesnenin adresine yönelik bir işaretçi `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="e4b46-111">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4b46-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4b46-112">Return Value</span></span>  
  
|<span data-ttu-id="e4b46-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4b46-113">HRESULT</span></span>|<span data-ttu-id="e4b46-114">Description</span><span class="sxs-lookup"><span data-stu-id="e4b46-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4b46-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4b46-115">S_OK</span></span>|<span data-ttu-id="e4b46-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e4b46-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="e4b46-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4b46-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4b46-118">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e4b46-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4b46-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4b46-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4b46-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e4b46-120">The call timed out.</span></span>|  
|<span data-ttu-id="e4b46-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4b46-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4b46-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e4b46-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4b46-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4b46-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4b46-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="e4b46-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4b46-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4b46-125">E_FAIL</span></span>|<span data-ttu-id="e4b46-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e4b46-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4b46-127">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e4b46-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4b46-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4b46-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4b46-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4b46-129">Remarks</span></span>  

 <span data-ttu-id="e4b46-130">Çağıran, bir bilinen derleme başvuruları kümesini döndürülen listeden dışlamayı tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="e4b46-130">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="e4b46-131">Bu küme parametresi tarafından tanımlanır `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="e4b46-131">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4b46-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4b46-132">Requirements</span></span>  

 <span data-ttu-id="e4b46-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4b46-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4b46-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4b46-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4b46-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e4b46-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4b46-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4b46-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b46-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4b46-137">See also</span></span>

- [<span data-ttu-id="e4b46-138">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4b46-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="e4b46-139">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4b46-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e4b46-140">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4b46-140">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)

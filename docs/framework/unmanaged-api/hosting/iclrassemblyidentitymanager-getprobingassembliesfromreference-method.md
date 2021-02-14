---
description: ': ICLRAssemblyIdentityManager:: Getprobing, Liesfromreference yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 38fcea460537ebed0e54103b460a48c2e58d8173
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431431"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="a45af-103">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a45af-103">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>

<span data-ttu-id="a45af-104">Belirtilen kimlik türüyle derleme tarafından başvurulan derleme kimlikleri için bir [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) numaralandırıcısı alır.</span><span class="sxs-lookup"><span data-stu-id="a45af-104">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a45af-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a45af-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a45af-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a45af-106">Parameters</span></span>  

 `dwMachineType`  
 <span data-ttu-id="a45af-107">'ndaki WinNT. h içinde tanımlanan işlemci mimarisini belirten geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="a45af-107">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a45af-108">'ndaki Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a45af-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="a45af-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="a45af-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="a45af-110">'ndaki Genellikle [ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) veya [ICLRAssemblyIdentityManager:: GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metoduna yapılan çağrıdan döndürülen donuk bir derleme bağlama kimliği.</span><span class="sxs-lookup"><span data-stu-id="a45af-110">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="a45af-111">dışı `ICLRProbingAssemblyEnum` Tarafından tanımlanan derlemenin başvurduğu derlemelere yönelik başvuruları içeren bir Numaralandırıcı için arabirim işaretçisi `pwzReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="a45af-111">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a45af-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a45af-112">Return Value</span></span>  
  
|<span data-ttu-id="a45af-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a45af-113">HRESULT</span></span>|<span data-ttu-id="a45af-114">Description</span><span class="sxs-lookup"><span data-stu-id="a45af-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a45af-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a45af-115">S_OK</span></span>|<span data-ttu-id="a45af-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a45af-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="a45af-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a45af-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a45af-118">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a45af-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a45af-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a45af-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a45af-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a45af-120">The call timed out.</span></span>|  
|<span data-ttu-id="a45af-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a45af-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a45af-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a45af-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a45af-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a45af-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a45af-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a45af-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a45af-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a45af-125">E_FAIL</span></span>|<span data-ttu-id="a45af-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a45af-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a45af-127">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a45af-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a45af-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a45af-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a45af-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a45af-129">Requirements</span></span>  

 <span data-ttu-id="a45af-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a45af-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a45af-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a45af-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a45af-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a45af-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a45af-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a45af-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a45af-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a45af-134">See also</span></span>

- [<span data-ttu-id="a45af-135">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a45af-135">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="a45af-136">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a45af-136">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a45af-137">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a45af-137">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)

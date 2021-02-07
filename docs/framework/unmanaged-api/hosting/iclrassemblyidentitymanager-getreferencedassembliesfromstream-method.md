---
description: ': ICLRAssemblyIdentityManager:: GetReferencedAssembliesFromStream yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9173587125e7b528e203dcb7e6a19d3e3f2fb990
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746119"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a><span data-ttu-id="ba146-103">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba146-103">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream Method</span></span>

<span data-ttu-id="ba146-104">Belirtilen akıştaki derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren bir [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) nesnesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ba146-104">Gets a pointer to an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba146-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba146-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba146-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba146-106">Parameters</span></span>  

 `pStream`  
 <span data-ttu-id="ba146-107">'ndaki `IStream` Değerlendirilecek derlemeyi içeren bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ba146-107">[in] An interface pointer to an `IStream` containing the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ba146-108">'ndaki Gelecekteki genişletilebilirlik için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ba146-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="ba146-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT, ortak dil çalışma zamanının (CLR) geçerli sürümünün desteklediği tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="ba146-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="ba146-110">'ndaki Dışlanacak derlemeler için derleme kimliği verilerini içeren [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) nesnesine yönelik bir işaretçi `ppReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="ba146-110">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that contains assembly identity data for the assemblies to be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="ba146-111">dışı İçindeki `ICLRReferenceAssemblyEnum` derlemeler hariç, içindeki derleme tarafından başvurulan derlemeler için derleme kimliği verilerini içeren bir nesnenin adresine yönelik bir işaretçi `pStream` `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="ba146-111">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in `pStream`, excluding the assemblies in `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba146-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba146-112">Return Value</span></span>  
  
|<span data-ttu-id="ba146-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ba146-113">HRESULT</span></span>|<span data-ttu-id="ba146-114">Description</span><span class="sxs-lookup"><span data-stu-id="ba146-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba146-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba146-115">S_OK</span></span>|<span data-ttu-id="ba146-116">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ba146-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="ba146-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ba146-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ba146-118">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ba146-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ba146-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ba146-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ba146-120">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ba146-120">The call timed out.</span></span>|  
|<span data-ttu-id="ba146-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ba146-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ba146-122">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ba146-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ba146-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ba146-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ba146-124">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ba146-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ba146-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ba146-125">E_FAIL</span></span>|<span data-ttu-id="ba146-126">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ba146-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ba146-127">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ba146-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ba146-128">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba146-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba146-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba146-129">Remarks</span></span>  

 <span data-ttu-id="ba146-130">Çağıran, bir bilinen derleme başvuruları kümesini döndürülen listeden dışlamayı tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="ba146-130">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="ba146-131">Bu küme tarafından tanımlanır `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="ba146-131">This set is defined by `pExcludeAssembliesList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba146-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba146-132">Requirements</span></span>  

 <span data-ttu-id="ba146-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba146-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba146-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ba146-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba146-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ba146-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba146-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba146-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba146-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba146-137">See also</span></span>

- [<span data-ttu-id="ba146-138">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba146-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="ba146-139">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba146-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="ba146-140">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba146-140">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)

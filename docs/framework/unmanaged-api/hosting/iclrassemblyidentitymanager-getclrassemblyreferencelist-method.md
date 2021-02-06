---
description: 'Şu konuda daha fazla bilgi edinin: ICLRAssemblyIdentityManager:: GetCLRAssemblyReferenceList yöntemi'
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Metodu
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
ms.openlocfilehash: 91f7b9eaacee559c5e404b5dda0f8b4201f91a66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649565"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="86719-103">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Metodu</span><span class="sxs-lookup"><span data-stu-id="86719-103">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>

<span data-ttu-id="86719-104">Sağlanan kısmi derleme kimlikleri listesinden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="86719-104">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86719-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86719-105">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86719-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86719-106">Parameters</span></span>  

 `ppwzAssemblyReferences`  
 <span data-ttu-id="86719-107">'ndaki "Ad, özellik = değer..." biçiminde null ile sonlandırılmış dizeler dizisi Bu, kısmi derleme kimliklerinin bir listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="86719-107">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="86719-108">'ndaki İçindeki öğe sayısı `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="86719-108">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="86719-109">dışı `ICLRAssemblyReferenceList` İçinde belirtilen derlemelerin listesi için derleme kimliği verilerini içeren bir nesneye yönelik arabirim işaretçisi `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="86719-109">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86719-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86719-110">Return Value</span></span>  
  
|<span data-ttu-id="86719-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86719-111">HRESULT</span></span>|<span data-ttu-id="86719-112">Description</span><span class="sxs-lookup"><span data-stu-id="86719-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86719-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="86719-113">S_OK</span></span>|<span data-ttu-id="86719-114">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="86719-114">The method returned successfully.</span></span>|  
|<span data-ttu-id="86719-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86719-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86719-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="86719-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86719-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86719-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86719-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="86719-118">The call timed out.</span></span>|  
|<span data-ttu-id="86719-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86719-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86719-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="86719-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86719-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86719-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86719-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="86719-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86719-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86719-123">E_FAIL</span></span>|<span data-ttu-id="86719-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="86719-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86719-125">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="86719-125">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86719-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="86719-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86719-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86719-127">Requirements</span></span>  

 <span data-ttu-id="86719-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86719-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86719-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="86719-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86719-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="86719-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86719-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86719-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86719-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86719-132">See also</span></span>

- [<span data-ttu-id="86719-133">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86719-133">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="86719-134">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86719-134">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)

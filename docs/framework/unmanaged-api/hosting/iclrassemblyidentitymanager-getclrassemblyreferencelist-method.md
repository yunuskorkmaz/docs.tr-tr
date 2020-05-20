---
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
ms.openlocfilehash: 7f09cb2264b21fdfbc892069f2c2f0a963b131f8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615975"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="5b51b-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Metodu</span><span class="sxs-lookup"><span data-stu-id="5b51b-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="5b51b-103">Sağlanan kısmi derleme kimlikleri listesinden bir [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) örneğine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="5b51b-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b51b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5b51b-104">Syntax</span></span>  
  
```cpp  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b51b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b51b-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="5b51b-106">'ndaki "Ad, özellik = değer..." biçiminde null ile sonlandırılmış dizeler dizisi Bu, kısmi derleme kimliklerinin bir listesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b51b-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="5b51b-107">'ndaki İçindeki öğe sayısı `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="5b51b-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="5b51b-108">dışı `ICLRAssemblyReferenceList`İçinde belirtilen derlemelerin listesi için derleme kimliği verilerini içeren bir nesneye yönelik arabirim işaretçisi `ppwzAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="5b51b-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b51b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b51b-109">Return Value</span></span>  
  
|<span data-ttu-id="5b51b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5b51b-110">HRESULT</span></span>|<span data-ttu-id="5b51b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5b51b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5b51b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5b51b-112">S_OK</span></span>|<span data-ttu-id="5b51b-113">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5b51b-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="5b51b-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5b51b-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5b51b-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5b51b-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5b51b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5b51b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5b51b-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5b51b-117">The call timed out.</span></span>|  
|<span data-ttu-id="5b51b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5b51b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5b51b-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5b51b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5b51b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5b51b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5b51b-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5b51b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5b51b-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5b51b-122">E_FAIL</span></span>|<span data-ttu-id="5b51b-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5b51b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5b51b-124">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5b51b-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5b51b-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5b51b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b51b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b51b-126">Requirements</span></span>  
 <span data-ttu-id="5b51b-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b51b-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b51b-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5b51b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b51b-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5b51b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b51b-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b51b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b51b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b51b-131">See also</span></span>

- [<span data-ttu-id="5b51b-132">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b51b-132">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="5b51b-133">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b51b-133">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)

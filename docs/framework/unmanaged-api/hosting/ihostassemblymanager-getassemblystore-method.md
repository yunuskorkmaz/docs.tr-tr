---
title: IHostAssemblyManager::GetAssemblyStore Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 91c9a92d83312efcfd90a15aa0a60cccb6b44d7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134731"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="2ae0e-102">IHostAssemblyManager::GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ae0e-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="2ae0e-103">Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae0e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ae0e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ae0e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ae0e-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="2ae0e-106">dışı `IHostAssemblyStore` örneğine yönelik bir işlev işaretçisi veya konak `IHostAssemblyStore`uygulamadıysanız null.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ae0e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2ae0e-107">Return Value</span></span>  
  
|<span data-ttu-id="2ae0e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ae0e-108">HRESULT</span></span>|<span data-ttu-id="2ae0e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ae0e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ae0e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ae0e-110">S_OK</span></span>|<span data-ttu-id="2ae0e-111">`GetAssemblyStore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="2ae0e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ae0e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ae0e-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ae0e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ae0e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ae0e-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-115">The call timed out.</span></span>|  
|<span data-ttu-id="2ae0e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ae0e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ae0e-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ae0e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ae0e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ae0e-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ae0e-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="2ae0e-120">E_FAIL</span></span>|<span data-ttu-id="2ae0e-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ae0e-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ae0e-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2ae0e-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="2ae0e-124">E_NOINTERFACE</span></span>|<span data-ttu-id="2ae0e-125">Ana bilgisayar `IHostAssemblyStore`bir uygulamasını sağlamıyor.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ae0e-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ae0e-126">Remarks</span></span>  
 <span data-ttu-id="2ae0e-127">`IHostAssemblyStore`, bir konağın CLR 'den bağımsız olarak derlemelere ve modüllere bağlanmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="2ae0e-128">Konaklar genellikle derlemelerin dosya sistemi dışındaki biçimlerden yüklenmesine izin vermek için derleme depoları sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ae0e-129">Ana bilgisayar `IHostAssemblyStore`uygulamadıysanız, `GetAssemblyStore` bir HRESULT değeri döndürmelidir ve `ppAssemblyStore` null olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ae0e-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ae0e-130">Requirements</span></span>  
 <span data-ttu-id="2ae0e-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ae0e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ae0e-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2ae0e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ae0e-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2ae0e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ae0e-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ae0e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae0e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ae0e-135">See also</span></span>

- [<span data-ttu-id="2ae0e-136">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ae0e-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="2ae0e-137">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ae0e-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

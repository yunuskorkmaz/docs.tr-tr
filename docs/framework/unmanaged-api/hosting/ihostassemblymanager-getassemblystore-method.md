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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62965fa928522052b6885769e02c0211ca8d3fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937942"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="a6dce-102">IHostAssemblyManager::GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6dce-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="a6dce-103">Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="a6dce-103">Gets an interface pointer to an [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6dce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6dce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6dce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6dce-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="a6dce-106">dışı `IHostAssemblyStore` Örnek için bir işlev işaretçisi veya ana bilgisayar uygulamadıysanız `IHostAssemblyStore`null.</span><span class="sxs-lookup"><span data-stu-id="a6dce-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6dce-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a6dce-107">Return Value</span></span>  
  
|<span data-ttu-id="a6dce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6dce-108">HRESULT</span></span>|<span data-ttu-id="a6dce-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6dce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a6dce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6dce-110">S_OK</span></span>|<span data-ttu-id="a6dce-111">`GetAssemblyStore`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a6dce-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="a6dce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a6dce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a6dce-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a6dce-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a6dce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a6dce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a6dce-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a6dce-115">The call timed out.</span></span>|  
|<span data-ttu-id="a6dce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a6dce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a6dce-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a6dce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a6dce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a6dce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a6dce-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a6dce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a6dce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a6dce-120">E_FAIL</span></span>|<span data-ttu-id="a6dce-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a6dce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a6dce-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a6dce-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a6dce-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a6dce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a6dce-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="a6dce-124">E_NOINTERFACE</span></span>|<span data-ttu-id="a6dce-125">Konak, uygulamasının bir uygulamasını `IHostAssemblyStore`sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a6dce-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6dce-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6dce-126">Remarks</span></span>  
 <span data-ttu-id="a6dce-127">`IHostAssemblyStore`bir konağın CLR 'den bağımsız olarak derlemelere ve modüllere bağlanmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6dce-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="a6dce-128">Konaklar genellikle derlemelerin dosya sistemi dışındaki biçimlerden yüklenmesine izin vermek için derleme depoları sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6dce-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6dce-129">Ana bilgisayar uygulamadıysanız `IHostAssemblyStore`, `GetAssemblyStore` E_NOINTERFACE HRESULT değeri döndürmelidir ve null olarak ayarlanmalıdır `ppAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="a6dce-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6dce-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6dce-130">Requirements</span></span>  
 <span data-ttu-id="a6dce-131">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6dce-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6dce-132">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a6dce-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6dce-133">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a6dce-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6dce-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6dce-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6dce-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6dce-135">See also</span></span>

- [<span data-ttu-id="a6dce-136">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6dce-136">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="a6dce-137">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6dce-137">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)

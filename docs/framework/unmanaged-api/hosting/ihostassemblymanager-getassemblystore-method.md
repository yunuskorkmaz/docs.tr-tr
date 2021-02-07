---
description: ': IHostAssemblyManager:: GetAssemblyStore yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5edfdc5481803ce0dd3a6f8f400b18e3f1600ea8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709119"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="3519e-103">IHostAssemblyManager::GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3519e-103">IHostAssemblyManager::GetAssemblyStore Method</span></span>

<span data-ttu-id="3519e-104">Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="3519e-104">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3519e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3519e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3519e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3519e-106">Parameters</span></span>  

 `ppAssemblyStore`  
 <span data-ttu-id="3519e-107">dışı Örnek için bir işlev işaretçisi `IHostAssemblyStore` veya ana bilgisayar uygulamadıysanız null `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="3519e-107">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3519e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3519e-108">Return Value</span></span>  
  
|<span data-ttu-id="3519e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3519e-109">HRESULT</span></span>|<span data-ttu-id="3519e-110">Description</span><span class="sxs-lookup"><span data-stu-id="3519e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3519e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3519e-111">S_OK</span></span>|<span data-ttu-id="3519e-112">`GetAssemblyStore` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3519e-112">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="3519e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3519e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3519e-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3519e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3519e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3519e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3519e-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3519e-116">The call timed out.</span></span>|  
|<span data-ttu-id="3519e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3519e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3519e-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3519e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3519e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3519e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3519e-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3519e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3519e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3519e-121">E_FAIL</span></span>|<span data-ttu-id="3519e-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3519e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3519e-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3519e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3519e-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3519e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3519e-125">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="3519e-125">E_NOINTERFACE</span></span>|<span data-ttu-id="3519e-126">Konak, uygulamasının bir uygulamasını sağlamaz `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="3519e-126">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3519e-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3519e-127">Remarks</span></span>  

 <span data-ttu-id="3519e-128">`IHostAssemblyStore` bir konağın CLR 'den bağımsız olarak derlemelere ve modüllere bağlanmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3519e-128">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="3519e-129">Konaklar genellikle derlemelerin dosya sistemi dışındaki biçimlerden yüklenmesine izin vermek için derleme depoları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3519e-129">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3519e-130">Konak uygulamadıysanız `IHostAssemblyStore` , `GetAssemblyStore` E_NOINTERFACE HRESULT değeri döndürmelidir ve `ppAssemblyStore` null olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3519e-130">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3519e-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3519e-131">Requirements</span></span>  

 <span data-ttu-id="3519e-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3519e-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3519e-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3519e-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3519e-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3519e-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3519e-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3519e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3519e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3519e-136">See also</span></span>

- [<span data-ttu-id="3519e-137">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3519e-137">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="3519e-138">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3519e-138">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)

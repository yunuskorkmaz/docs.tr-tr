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
ms.openlocfilehash: 587861529c340fad9fd817b904e4d3651b236e8d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805080"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="0ca78-102">IHostAssemblyManager::GetAssemblyStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ca78-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>
<span data-ttu-id="0ca78-103">Konak tarafından yüklenen derlemelerin listesini temsil eden bir [IHostAssemblyStore](ihostassemblystore-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="0ca78-103">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca78-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0ca78-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ca78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ca78-105">Parameters</span></span>  
 `ppAssemblyStore`  
 <span data-ttu-id="0ca78-106">dışı Örnek için bir işlev işaretçisi `IHostAssemblyStore` veya ana bilgisayar uygulamadıysanız null `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="0ca78-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ca78-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0ca78-107">Return Value</span></span>  
  
|<span data-ttu-id="0ca78-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ca78-108">HRESULT</span></span>|<span data-ttu-id="0ca78-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ca78-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ca78-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ca78-110">S_OK</span></span>|<span data-ttu-id="0ca78-111">`GetAssemblyStore`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0ca78-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="0ca78-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ca78-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ca78-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0ca78-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ca78-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ca78-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ca78-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0ca78-115">The call timed out.</span></span>|  
|<span data-ttu-id="0ca78-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ca78-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ca78-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0ca78-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ca78-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ca78-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ca78-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0ca78-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ca78-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ca78-120">E_FAIL</span></span>|<span data-ttu-id="0ca78-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0ca78-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ca78-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0ca78-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ca78-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ca78-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ca78-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="0ca78-124">E_NOINTERFACE</span></span>|<span data-ttu-id="0ca78-125">Konak, uygulamasının bir uygulamasını sağlamaz `IHostAssemblyStore` .</span><span class="sxs-lookup"><span data-stu-id="0ca78-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ca78-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ca78-126">Remarks</span></span>  
 <span data-ttu-id="0ca78-127">`IHostAssemblyStore`bir konağın CLR 'den bağımsız olarak derlemelere ve modüllere bağlanmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ca78-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="0ca78-128">Konaklar genellikle derlemelerin dosya sistemi dışındaki biçimlerden yüklenmesine izin vermek için derleme depoları sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ca78-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca78-129">Konak uygulamadıysanız `IHostAssemblyStore` , `GetAssemblyStore` E_NOINTERFACE HRESULT değeri döndürmelidir ve `ppAssemblyStore` null olarak ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ca78-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ca78-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ca78-130">Requirements</span></span>  
 <span data-ttu-id="0ca78-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ca78-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca78-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0ca78-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ca78-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0ca78-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ca78-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ca78-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca78-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ca78-135">See also</span></span>

- [<span data-ttu-id="0ca78-136">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ca78-136">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="0ca78-137">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ca78-137">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)

---
title: ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3174cf3b4f4f4ac4b2c8e69030357eb1e46cf3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197834"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="59dc1-102">ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59dc1-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="59dc1-103">Başlangıç bayrakları ve çalışma zamanı'nı başlatmak için kullanılacak ana bilgisayar yapılandırma dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="59dc1-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="59dc1-104">Bu yöntem yerine geçer kullanımını `startupFlags` parametresinde [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="59dc1-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59dc1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59dc1-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59dc1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59dc1-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="59dc1-107">[in] Ayarlamak için konak başlangıç bayraklar.</span><span class="sxs-lookup"><span data-stu-id="59dc1-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="59dc1-108">İle aynı bayrak olarak kullanmak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="59dc1-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="59dc1-109">[in] Ana bilgisayar yapılandırma dosyası ayarlamak için dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="59dc1-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59dc1-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="59dc1-110">Return Value</span></span>  
 <span data-ttu-id="59dc1-111">Bu yöntem aşağıdaki özel HRESULT döndürür yöntemi hatayı belirtmek HRESULT hata yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="59dc1-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="59dc1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="59dc1-112">HRESULT</span></span>|<span data-ttu-id="59dc1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="59dc1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="59dc1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="59dc1-114">S_OK</span></span>|<span data-ttu-id="59dc1-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="59dc1-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59dc1-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="59dc1-116">Remarks</span></span>  
 <span data-ttu-id="59dc1-117">Çok iş parçacıklı bir konak, bu yönteme çağrıları eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="59dc1-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="59dc1-118">Aksi takdirde, iş parçacığı bir çağrı `SetStartupFlags` B iş parçacığı çağrı tamamlandıktan sonra yöntemi `SetStartupFlags` ve çalışma zamanı iş parçacığı B başlatılmadan önce.</span><span class="sxs-lookup"><span data-stu-id="59dc1-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59dc1-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59dc1-119">Requirements</span></span>  
 <span data-ttu-id="59dc1-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59dc1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59dc1-121">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="59dc1-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="59dc1-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="59dc1-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="59dc1-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="59dc1-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="59dc1-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59dc1-124">See also</span></span>

- [<span data-ttu-id="59dc1-125">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59dc1-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="59dc1-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="59dc1-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="59dc1-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="59dc1-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

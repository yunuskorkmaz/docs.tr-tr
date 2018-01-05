---
title: "ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.SetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69306210ae4e957562d0bda88159d0506bca3877
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="eda98-102">ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eda98-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="eda98-103">Başlangıç bayrakları ve çalışma zamanı başlatmak için kullanılan ana bilgisayar yapılandırma dosyası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eda98-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="eda98-104">Bu yöntem kullanımını yerini `startupFlags` parametresinde [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="eda98-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda98-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eda98-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eda98-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eda98-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="eda98-107">[in] Ayarlamak için konak başlangıç bayraklar.</span><span class="sxs-lookup"><span data-stu-id="eda98-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="eda98-108">Olarak aynı bayraklarıyla kullanmak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="eda98-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="eda98-109">[in] Ayarlamak için ana bilgisayar yapılandırma dosyası dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="eda98-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eda98-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eda98-110">Return Value</span></span>  
 <span data-ttu-id="eda98-111">Bu yöntem aşağıdaki belirli HRESULT döndürür yöntemi hatayı belirtmek HRESULT hata yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="eda98-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="eda98-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eda98-112">HRESULT</span></span>|<span data-ttu-id="eda98-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eda98-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eda98-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="eda98-114">S_OK</span></span>|<span data-ttu-id="eda98-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="eda98-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eda98-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eda98-116">Remarks</span></span>  
 <span data-ttu-id="eda98-117">Birden çok iş parçacıklı bir konak, bu yönteme çağrıları eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eda98-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="eda98-118">Aksi durumda, iş parçacığı A çağırabilirsiniz `SetStartupFlags` iş parçacığı B çağrısı tamamlandığında yöntemi `SetStartupFlags` ve iş parçacığı B çalışma zamanı başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="eda98-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda98-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eda98-119">Requirements</span></span>  
 <span data-ttu-id="eda98-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eda98-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eda98-121">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="eda98-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="eda98-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="eda98-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eda98-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eda98-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda98-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eda98-124">See Also</span></span>  
 [<span data-ttu-id="eda98-125">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eda98-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="eda98-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eda98-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="eda98-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="eda98-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

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
ms.openlocfilehash: 1732073b9799453bd32447e7a688b0280e66f1ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="9d56b-102">ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d56b-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="9d56b-103">Başlangıç bayrakları ve çalışma zamanı başlatmak için kullanılan ana bilgisayar yapılandırma dosyası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9d56b-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="9d56b-104">Bu yöntem kullanımını yerini `startupFlags` parametresinde [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="9d56b-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d56b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d56b-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d56b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d56b-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="9d56b-107">[in] Ayarlamak için konak başlangıç bayraklar.</span><span class="sxs-lookup"><span data-stu-id="9d56b-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="9d56b-108">Olarak aynı bayraklarıyla kullanmak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) işlevleri.</span><span class="sxs-lookup"><span data-stu-id="9d56b-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="9d56b-109">[in] Ayarlamak için ana bilgisayar yapılandırma dosyası dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="9d56b-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d56b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9d56b-110">Return Value</span></span>  
 <span data-ttu-id="9d56b-111">Bu yöntem aşağıdaki belirli HRESULT döndürür yöntemi hatayı belirtmek HRESULT hata yanı sıra.</span><span class="sxs-lookup"><span data-stu-id="9d56b-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9d56b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d56b-112">HRESULT</span></span>|<span data-ttu-id="9d56b-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d56b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d56b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d56b-114">S_OK</span></span>|<span data-ttu-id="9d56b-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9d56b-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d56b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d56b-116">Remarks</span></span>  
 <span data-ttu-id="9d56b-117">Birden çok iş parçacıklı bir konak, bu yönteme çağrıları eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d56b-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="9d56b-118">Aksi durumda, iş parçacığı A çağırabilirsiniz `SetStartupFlags` iş parçacığı B çağrısı tamamlandığında yöntemi `SetStartupFlags` ve iş parçacığı B çalışma zamanı başlamadan önce.</span><span class="sxs-lookup"><span data-stu-id="9d56b-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d56b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d56b-119">Requirements</span></span>  
 <span data-ttu-id="9d56b-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d56b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d56b-121">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9d56b-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d56b-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9d56b-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d56b-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d56b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d56b-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d56b-124">See Also</span></span>  
 [<span data-ttu-id="9d56b-125">Iclrruntimeınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d56b-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="9d56b-126">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d56b-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="9d56b-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="9d56b-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

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
ms.openlocfilehash: 36851ac4573d0d65caffaa3f82a1f6fc8440a2d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092748"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="94574-102">ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94574-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="94574-103">Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="94574-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="94574-104">Bu yöntem [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) işlevlerinde `startupFlags` parametresinin kullanımını yerini alır.</span><span class="sxs-lookup"><span data-stu-id="94574-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94574-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94574-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94574-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94574-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="94574-107">'ndaki Ayarlanacak konak başlangıç bayrakları.</span><span class="sxs-lookup"><span data-stu-id="94574-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="94574-108">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) işlevleriyle aynı bayrakları kullanın.</span><span class="sxs-lookup"><span data-stu-id="94574-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="94574-109">'ndaki Ayarlanacak ana bilgisayar yapılandırma dosyasının dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="94574-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94574-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="94574-110">Return Value</span></span>  
 <span data-ttu-id="94574-111">Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="94574-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="94574-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94574-112">HRESULT</span></span>|<span data-ttu-id="94574-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94574-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94574-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="94574-114">S_OK</span></span>|<span data-ttu-id="94574-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="94574-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94574-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94574-116">Remarks</span></span>  
 <span data-ttu-id="94574-117">Çok iş parçacıklı bir ana bilgisayar çağrıları bu yöntemle eşitlemelidir.</span><span class="sxs-lookup"><span data-stu-id="94574-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="94574-118">Aksi takdirde, A iş parçacığı B, bir `SetStartupFlags` çağrısını tamamladıktan sonra ve iş parçacığı B çalışma zamanını başlatmadan önce `SetStartupFlags` yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="94574-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94574-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94574-119">Requirements</span></span>  
 <span data-ttu-id="94574-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94574-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94574-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="94574-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="94574-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="94574-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94574-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94574-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94574-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94574-124">See also</span></span>

- [<span data-ttu-id="94574-125">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94574-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="94574-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94574-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="94574-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="94574-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

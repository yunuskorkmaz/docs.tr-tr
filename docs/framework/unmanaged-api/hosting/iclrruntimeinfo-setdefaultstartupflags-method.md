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
ms.openlocfilehash: aa02d42511a863434fef236f90afae2c5417a78d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504023"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="7ff2e-102">ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ff2e-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="7ff2e-103">Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="7ff2e-104">Bu yöntem `startupFlags` , [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevlerinde parametresinin kullanımını yerini alır.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ff2e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7ff2e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ff2e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ff2e-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="7ff2e-107">'ndaki Ayarlanacak konak başlangıç bayrakları.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="7ff2e-108">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevleriyle aynı bayrakları kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-108">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="7ff2e-109">'ndaki Ayarlanacak ana bilgisayar yapılandırma dosyasının dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ff2e-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7ff2e-110">Return Value</span></span>  
 <span data-ttu-id="7ff2e-111">Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7ff2e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ff2e-112">HRESULT</span></span>|<span data-ttu-id="7ff2e-113">Description</span><span class="sxs-lookup"><span data-stu-id="7ff2e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ff2e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ff2e-114">S_OK</span></span>|<span data-ttu-id="7ff2e-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ff2e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ff2e-116">Remarks</span></span>  
 <span data-ttu-id="7ff2e-117">Çok iş parçacıklı bir ana bilgisayar çağrıları bu yöntemle eşitlemelidir.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="7ff2e-118">Aksi takdirde, A iş parçacığı b iş parçacığını `SetStartupFlags` başlattıktan önce ve ' a çağrı tamamladıktan sonra yöntemini çağırabilir `SetStartupFlags` .</span><span class="sxs-lookup"><span data-stu-id="7ff2e-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff2e-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ff2e-119">Requirements</span></span>  
 <span data-ttu-id="7ff2e-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff2e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff2e-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7ff2e-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7ff2e-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7ff2e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ff2e-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff2e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff2e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff2e-124">See also</span></span>

- [<span data-ttu-id="7ff2e-125">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ff2e-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7ff2e-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ff2e-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7ff2e-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="7ff2e-127">Hosting</span></span>](index.md)

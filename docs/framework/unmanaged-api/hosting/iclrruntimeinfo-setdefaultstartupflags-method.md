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
ms.openlocfilehash: 8020db491c3b66be38a9f6cbcb7551721859dcd5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723122"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="937b6-102">ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="937b6-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>

<span data-ttu-id="937b6-103">Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="937b6-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="937b6-104">Bu yöntem `startupFlags` , [CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevlerinde parametresinin kullanımını yerini alır.</span><span class="sxs-lookup"><span data-stu-id="937b6-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="937b6-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="937b6-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="937b6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="937b6-106">Parameters</span></span>  

 `dwStartupFlags`  
 <span data-ttu-id="937b6-107">'ndaki Ayarlanacak konak başlangıç bayrakları.</span><span class="sxs-lookup"><span data-stu-id="937b6-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="937b6-108">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevleriyle aynı bayrakları kullanın.</span><span class="sxs-lookup"><span data-stu-id="937b6-108">Use the same flags as with the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="937b6-109">'ndaki Ayarlanacak ana bilgisayar yapılandırma dosyasının dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="937b6-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="937b6-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="937b6-110">Return Value</span></span>  

 <span data-ttu-id="937b6-111">Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="937b6-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="937b6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="937b6-112">HRESULT</span></span>|<span data-ttu-id="937b6-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="937b6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="937b6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="937b6-114">S_OK</span></span>|<span data-ttu-id="937b6-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="937b6-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="937b6-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="937b6-116">Remarks</span></span>  

 <span data-ttu-id="937b6-117">Çok iş parçacıklı bir ana bilgisayar çağrıları bu yöntemle eşitlemelidir.</span><span class="sxs-lookup"><span data-stu-id="937b6-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="937b6-118">Aksi takdirde, A iş parçacığı b iş parçacığını `SetStartupFlags` başlattıktan önce ve ' a çağrı tamamladıktan sonra yöntemini çağırabilir `SetStartupFlags` .</span><span class="sxs-lookup"><span data-stu-id="937b6-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="937b6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="937b6-119">Requirements</span></span>  

 <span data-ttu-id="937b6-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="937b6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="937b6-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="937b6-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="937b6-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="937b6-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="937b6-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="937b6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="937b6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="937b6-124">See also</span></span>

- [<span data-ttu-id="937b6-125">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="937b6-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="937b6-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="937b6-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="937b6-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="937b6-127">Hosting</span></span>](index.md)

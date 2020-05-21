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
ms.openlocfilehash: 7d201962976d198372226eb686696fcdccf3eb69
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762168"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="0aec3-102">ICLRRuntimeInfo::SetDefaultStartupFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0aec3-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="0aec3-103">Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0aec3-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="0aec3-104">Bu yöntem `startupFlags` , [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevlerinde parametresinin kullanımını yerini alır.</span><span class="sxs-lookup"><span data-stu-id="0aec3-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aec3-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0aec3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aec3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0aec3-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="0aec3-107">'ndaki Ayarlanacak konak başlangıç bayrakları.</span><span class="sxs-lookup"><span data-stu-id="0aec3-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="0aec3-108">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ve [CorBindToRuntimeHost](corbindtoruntimehost-function.md) işlevleriyle aynı bayrakları kullanın.</span><span class="sxs-lookup"><span data-stu-id="0aec3-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="0aec3-109">'ndaki Ayarlanacak ana bilgisayar yapılandırma dosyasının dizin yolu.</span><span class="sxs-lookup"><span data-stu-id="0aec3-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0aec3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0aec3-110">Return Value</span></span>  
 <span data-ttu-id="0aec3-111">Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="0aec3-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0aec3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0aec3-112">HRESULT</span></span>|<span data-ttu-id="0aec3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0aec3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0aec3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="0aec3-114">S_OK</span></span>|<span data-ttu-id="0aec3-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0aec3-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aec3-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0aec3-116">Remarks</span></span>  
 <span data-ttu-id="0aec3-117">Çok iş parçacıklı bir ana bilgisayar çağrıları bu yöntemle eşitlemelidir.</span><span class="sxs-lookup"><span data-stu-id="0aec3-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="0aec3-118">Aksi takdirde, A iş parçacığı b iş parçacığını `SetStartupFlags` başlattıktan önce ve ' a çağrı tamamladıktan sonra yöntemini çağırabilir `SetStartupFlags` .</span><span class="sxs-lookup"><span data-stu-id="0aec3-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aec3-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0aec3-119">Requirements</span></span>  
 <span data-ttu-id="0aec3-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aec3-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aec3-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="0aec3-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0aec3-122">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0aec3-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0aec3-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aec3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aec3-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0aec3-124">See also</span></span>

- [<span data-ttu-id="0aec3-125">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0aec3-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0aec3-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0aec3-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="0aec3-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="0aec3-127">Hosting</span></span>](index.md)

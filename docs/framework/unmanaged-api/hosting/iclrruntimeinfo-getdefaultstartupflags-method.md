---
title: ICLRRuntimeInfo::GetDefaultStartupFlags Metodu
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 0ce822533b0699f3467dc08044aa4dab59285a77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120308"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="f65d7-102">ICLRRuntimeInfo::GetDefaultStartupFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="f65d7-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="f65d7-103">Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını alır.</span><span class="sxs-lookup"><span data-stu-id="f65d7-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f65d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f65d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f65d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f65d7-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="f65d7-106">dışı Şu anda ayarlanmış olan ana bilgisayar başlatma bayraklarının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f65d7-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="f65d7-107">dışı Geçerli ana bilgisayar yapılandırma dosyasının dizin yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f65d7-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="f65d7-108">[in, out] Girişte, arabellek taşmalarını önlemek için `pwzHostConfigFile`boyutu.</span><span class="sxs-lookup"><span data-stu-id="f65d7-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="f65d7-109">`pwzHostConfigFile` null ise, yöntemi ön ayırma için gereken `pwzHostConfigFile` boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f65d7-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f65d7-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f65d7-110">Return Value</span></span>  
 <span data-ttu-id="f65d7-111">Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f65d7-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f65d7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f65d7-112">HRESULT</span></span>|<span data-ttu-id="f65d7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f65d7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f65d7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f65d7-114">S_OK</span></span>|<span data-ttu-id="f65d7-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f65d7-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f65d7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f65d7-116">Remarks</span></span>  
 <span data-ttu-id="f65d7-117">Bu yöntem, varsayılan bayrak değerlerini (`STARTUP_CONCURRENT_GC` ve `NULL`) ya da bu çalışma zamanına bağlıysa `CorBind*` [metotlarından herhangi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)biri tarafından ayarlanan değerler tarafından belirtilen değerleri (ve) veya geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="f65d7-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f65d7-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f65d7-118">Requirements</span></span>  
 <span data-ttu-id="f65d7-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f65d7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f65d7-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f65d7-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f65d7-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f65d7-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f65d7-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f65d7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f65d7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f65d7-123">See also</span></span>

- [<span data-ttu-id="f65d7-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f65d7-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f65d7-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f65d7-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f65d7-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="f65d7-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

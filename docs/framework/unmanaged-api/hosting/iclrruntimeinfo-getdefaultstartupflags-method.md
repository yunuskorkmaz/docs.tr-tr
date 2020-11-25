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
ms.openlocfilehash: 2f828a3720f7313ee9cb851c6adae78bd5ea4fe8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732104"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="7bdf3-102">ICLRRuntimeInfo::GetDefaultStartupFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="7bdf3-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>

<span data-ttu-id="7bdf3-103">Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını alır.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bdf3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7bdf3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bdf3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bdf3-105">Parameters</span></span>  

 `pdwStartupFlags`  
 <span data-ttu-id="7bdf3-106">dışı Şu anda ayarlanmış olan ana bilgisayar başlatma bayraklarının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="7bdf3-107">dışı Geçerli ana bilgisayar yapılandırma dosyasının dizin yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="7bdf3-108">[in, out] Girişte, `pwzHostConfigFile` arabellek taşmalarını önlemek için, boyutu.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="7bdf3-109">`pwzHostConfigFile`Null ise, yöntemi `pwzHostConfigFile` ön ayırma için gereken boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bdf3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7bdf3-110">Return Value</span></span>  

 <span data-ttu-id="7bdf3-111">Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7bdf3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bdf3-112">HRESULT</span></span>|<span data-ttu-id="7bdf3-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bdf3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bdf3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bdf3-114">S_OK</span></span>|<span data-ttu-id="7bdf3-115">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bdf3-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bdf3-116">Remarks</span></span>  

 <span data-ttu-id="7bdf3-117">Bu yöntem, varsayılan bayrak değerlerini ( `STARTUP_CONCURRENT_GC` ve `NULL` ) ya da [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md) `CorBind*` Bu çalışma zamanına bağlılarsa yöntemlerin herhangi biri tarafından ayarlanan değerleri döndürür (ve) veya bir önceki çağrı tarafından belirtilen değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bdf3-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bdf3-118">Requirements</span></span>  

 <span data-ttu-id="7bdf3-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bdf3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bdf3-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7bdf3-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7bdf3-121">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7bdf3-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bdf3-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bdf3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bdf3-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bdf3-123">See also</span></span>

- [<span data-ttu-id="7bdf3-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bdf3-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="7bdf3-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7bdf3-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7bdf3-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="7bdf3-126">Hosting</span></span>](index.md)

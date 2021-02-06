---
description: ': ICLRRuntimeInfo:: GetDefaultStartupFlags Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c6afb19319fd24d499c2c216f2ce0adc2e7a886c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637187"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="c3d72-103">ICLRRuntimeInfo::GetDefaultStartupFlags Metodu</span><span class="sxs-lookup"><span data-stu-id="c3d72-103">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>

<span data-ttu-id="c3d72-104">Çalışma zamanını başlatmak için kullanılacak başlangıç bayraklarını ve ana bilgisayar yapılandırma dosyasını alır.</span><span class="sxs-lookup"><span data-stu-id="c3d72-104">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d72-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3d72-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3d72-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3d72-106">Parameters</span></span>  

 `pdwStartupFlags`  
 <span data-ttu-id="c3d72-107">dışı Şu anda ayarlanmış olan ana bilgisayar başlatma bayraklarının işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c3d72-107">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="c3d72-108">dışı Geçerli ana bilgisayar yapılandırma dosyasının dizin yoluna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3d72-108">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="c3d72-109">[in, out] Girişte, `pwzHostConfigFile` arabellek taşmalarını önlemek için, boyutu.</span><span class="sxs-lookup"><span data-stu-id="c3d72-109">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="c3d72-110">`pwzHostConfigFile`Null ise, yöntemi `pwzHostConfigFile` ön ayırma için gereken boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3d72-110">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3d72-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3d72-111">Return Value</span></span>  

 <span data-ttu-id="c3d72-112">Bu yöntem, aşağıdaki belirli HRESULT 'yi ve Yöntem hatasını belirten HRESULT hatalarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3d72-112">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c3d72-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3d72-113">HRESULT</span></span>|<span data-ttu-id="c3d72-114">Description</span><span class="sxs-lookup"><span data-stu-id="c3d72-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c3d72-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="c3d72-115">S_OK</span></span>|<span data-ttu-id="c3d72-116">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c3d72-116">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3d72-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3d72-117">Remarks</span></span>  

 <span data-ttu-id="c3d72-118">Bu yöntem, varsayılan bayrak değerlerini ( `STARTUP_CONCURRENT_GC` ve `NULL` ) ya da [](iclrruntimeinfo-setdefaultstartupflags-method.md) `CorBind*` Bu çalışma zamanına bağlılarsa yöntemlerin herhangi biri tarafından ayarlanan değerleri döndürür (ve) veya bir önceki çağrı tarafından belirtilen değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3d72-118">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3d72-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3d72-119">Requirements</span></span>  

 <span data-ttu-id="c3d72-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3d72-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3d72-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c3d72-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c3d72-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c3d72-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3d72-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3d72-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3d72-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3d72-124">See also</span></span>

- [<span data-ttu-id="c3d72-125">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3d72-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c3d72-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c3d72-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c3d72-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="c3d72-127">Hosting</span></span>](index.md)

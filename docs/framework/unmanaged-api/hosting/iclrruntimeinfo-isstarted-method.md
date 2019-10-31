---
title: ICLRRuntimeInfo::IsStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
ms.openlocfilehash: 34590744407b25d7d53c06c452fff5bac2a95246
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136381"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="96547-102">ICLRRuntimeInfo::IsStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96547-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="96547-103">Çalışma zamanının başlatıldığını (yani, [ICLRRuntimeHost:: Start yönteminin](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) çağrıldığından ve başarılı olup olmadığını) gösterir.</span><span class="sxs-lookup"><span data-stu-id="96547-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96547-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96547-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96547-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96547-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="96547-106">[out] Bu çalışma zamanı başlatılmışsa `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="96547-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="96547-107">dışı Çalışma zamanını başlatmak için kullanılan bayrakları döndürür.</span><span class="sxs-lookup"><span data-stu-id="96547-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96547-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="96547-108">Return Value</span></span>  
 <span data-ttu-id="96547-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="96547-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="96547-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96547-110">HRESULT</span></span>|<span data-ttu-id="96547-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96547-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96547-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="96547-112">S_OK</span></span>|<span data-ttu-id="96547-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="96547-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="96547-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="96547-114">E_NOTIMPL</span></span>|<span data-ttu-id="96547-115">Ortak dil çalışma zamanı (CLR) sürümü .NET Framework 4 ' teki CLR sürümünden daha eski.</span><span class="sxs-lookup"><span data-stu-id="96547-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96547-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96547-116">Remarks</span></span>  
 <span data-ttu-id="96547-117">Bu yöntem, .NET Framework 4 ' teki CLR sürümünden önceki CLR sürümleriyle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="96547-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96547-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96547-118">Requirements</span></span>  
 <span data-ttu-id="96547-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96547-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96547-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="96547-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="96547-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="96547-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96547-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96547-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96547-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96547-123">See also</span></span>

- [<span data-ttu-id="96547-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96547-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="96547-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="96547-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="96547-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="96547-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

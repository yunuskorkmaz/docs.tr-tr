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
ms.openlocfilehash: 1dfeb6101a6b8e33ab2fe35f318087d7f1834b6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714893"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="f9397-102">ICLRRuntimeInfo::IsStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f9397-102">ICLRRuntimeInfo::IsStarted Method</span></span>

<span data-ttu-id="f9397-103">Çalışma zamanının başlatıldığını (yani, [ICLRRuntimeHost:: Start yönteminin](iclrruntimehost-start-method.md) çağrıldığından ve başarılı olup olmadığını) gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9397-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9397-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f9397-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9397-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9397-105">Parameters</span></span>  

 `pbStarted`  
 <span data-ttu-id="f9397-106">[out] `true` Bu çalışma zamanı başlatılmışsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="f9397-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="f9397-107">dışı Çalışma zamanını başlatmak için kullanılan bayrakları döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9397-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9397-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f9397-108">Return Value</span></span>  

 <span data-ttu-id="f9397-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="f9397-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f9397-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9397-110">HRESULT</span></span>|<span data-ttu-id="f9397-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f9397-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9397-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9397-112">S_OK</span></span>|<span data-ttu-id="f9397-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f9397-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f9397-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f9397-114">E_NOTIMPL</span></span>|<span data-ttu-id="f9397-115">Ortak dil çalışma zamanı (CLR) sürümü .NET Framework 4 ' teki CLR sürümünden daha eski.</span><span class="sxs-lookup"><span data-stu-id="f9397-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9397-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9397-116">Remarks</span></span>  

 <span data-ttu-id="f9397-117">Bu yöntem, .NET Framework 4 ' teki CLR sürümünden önceki CLR sürümleriyle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="f9397-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9397-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9397-118">Requirements</span></span>  

 <span data-ttu-id="f9397-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9397-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9397-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f9397-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f9397-121">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f9397-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f9397-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9397-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9397-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9397-123">See also</span></span>

- [<span data-ttu-id="f9397-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9397-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f9397-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f9397-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f9397-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="f9397-126">Hosting</span></span>](index.md)

---
description: ': ICLRRuntimeInfo:: IsStarted yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 22059ecbded9eae9659cdaae8b9b92f2d7df0650
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753854"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="3a789-103">ICLRRuntimeInfo::IsStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a789-103">ICLRRuntimeInfo::IsStarted Method</span></span>

<span data-ttu-id="3a789-104">Çalışma zamanının başlatıldığını (yani, [ICLRRuntimeHost:: Start yönteminin](iclrruntimehost-start-method.md) çağrıldığından ve başarılı olup olmadığını) gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a789-104">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a789-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a789-105">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a789-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a789-106">Parameters</span></span>  

 `pbStarted`  
 <span data-ttu-id="3a789-107">[out] `true` Bu çalışma zamanı başlatılmışsa; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="3a789-107">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="3a789-108">dışı Çalışma zamanını başlatmak için kullanılan bayrakları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a789-108">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a789-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3a789-109">Return Value</span></span>  

 <span data-ttu-id="3a789-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a789-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3a789-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a789-111">HRESULT</span></span>|<span data-ttu-id="3a789-112">Description</span><span class="sxs-lookup"><span data-stu-id="3a789-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a789-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a789-113">S_OK</span></span>|<span data-ttu-id="3a789-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3a789-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="3a789-115">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3a789-115">E_NOTIMPL</span></span>|<span data-ttu-id="3a789-116">Ortak dil çalışma zamanı (CLR) sürümü .NET Framework 4 ' teki CLR sürümünden daha eski.</span><span class="sxs-lookup"><span data-stu-id="3a789-116">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a789-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a789-117">Remarks</span></span>  

 <span data-ttu-id="3a789-118">Bu yöntem, .NET Framework 4 ' teki CLR sürümünden önceki CLR sürümleriyle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="3a789-118">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a789-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a789-119">Requirements</span></span>  

 <span data-ttu-id="3a789-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a789-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a789-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="3a789-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3a789-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3a789-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a789-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a789-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a789-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a789-124">See also</span></span>

- [<span data-ttu-id="3a789-125">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a789-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="3a789-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3a789-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="3a789-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="3a789-127">Hosting</span></span>](index.md)

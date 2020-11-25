---
title: ICLRRuntimeHost::GetCurrentAppDomainId Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 2b1c9e99604664c99960a0741de6eae6b38fe963
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728855"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="a1e92-102">ICLRRuntimeHost::GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1e92-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>

<span data-ttu-id="a1e92-103"><xref:System.AppDomain>Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="a1e92-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1e92-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a1e92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1e92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1e92-105">Parameters</span></span>  

 `pdwAppDomainId`  
 <span data-ttu-id="a1e92-106">dışı <xref:System.AppDomain> Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a1e92-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1e92-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a1e92-107">Return Value</span></span>  
  
|<span data-ttu-id="a1e92-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1e92-108">HRESULT</span></span>|<span data-ttu-id="a1e92-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1e92-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1e92-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1e92-110">S_OK</span></span>|<span data-ttu-id="a1e92-111">`GetCurrentAppDomainId` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a1e92-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="a1e92-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1e92-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1e92-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a1e92-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1e92-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1e92-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1e92-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a1e92-115">The call timed out.</span></span>|  
|<span data-ttu-id="a1e92-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1e92-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1e92-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a1e92-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1e92-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1e92-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1e92-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a1e92-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1e92-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1e92-120">E_FAIL</span></span>|<span data-ttu-id="a1e92-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a1e92-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1e92-122">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a1e92-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1e92-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1e92-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1e92-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1e92-124">Remarks</span></span>  

 <span data-ttu-id="a1e92-125">`pdwAppDomainId`Parametresi <xref:System.AppDomain.Id%2A> , <xref:System.AppDomain> geçerli iş parçacığının yürütüldüğü öğesinin özelliğinin değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a1e92-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1e92-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1e92-126">Requirements</span></span>  

 <span data-ttu-id="a1e92-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1e92-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e92-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1e92-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1e92-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a1e92-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1e92-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e92-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e92-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1e92-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="a1e92-132">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1e92-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

---
description: ': ICLRRuntimeHost:: GetCurrentAppDomainId yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 88d5288e2e8ee7d8d1f5430261e21052334240be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799738"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="85264-103">ICLRRuntimeHost::GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85264-103">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>

<span data-ttu-id="85264-104"><xref:System.AppDomain>Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="85264-104">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85264-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85264-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85264-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85264-106">Parameters</span></span>  

 `pdwAppDomainId`  
 <span data-ttu-id="85264-107">dışı <xref:System.AppDomain> Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="85264-107">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85264-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="85264-108">Return Value</span></span>  
  
|<span data-ttu-id="85264-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85264-109">HRESULT</span></span>|<span data-ttu-id="85264-110">Description</span><span class="sxs-lookup"><span data-stu-id="85264-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85264-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="85264-111">S_OK</span></span>|<span data-ttu-id="85264-112">`GetCurrentAppDomainId` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="85264-112">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="85264-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="85264-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="85264-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="85264-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="85264-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="85264-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="85264-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="85264-116">The call timed out.</span></span>|  
|<span data-ttu-id="85264-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="85264-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="85264-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="85264-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="85264-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="85264-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="85264-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="85264-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="85264-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="85264-121">E_FAIL</span></span>|<span data-ttu-id="85264-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="85264-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="85264-123">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="85264-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="85264-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="85264-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85264-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85264-125">Remarks</span></span>  

 <span data-ttu-id="85264-126">`pdwAppDomainId`Parametresi <xref:System.AppDomain.Id%2A> , <xref:System.AppDomain> geçerli iş parçacığının yürütüldüğü öğesinin özelliğinin değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="85264-126">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85264-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85264-127">Requirements</span></span>  

 <span data-ttu-id="85264-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85264-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85264-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="85264-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85264-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="85264-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85264-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85264-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85264-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85264-132">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="85264-133">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85264-133">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

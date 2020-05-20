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
ms.openlocfilehash: 1c667b19ac4bfa0bea95b85cf099906e351e5b71
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703675"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="0e962-102">ICLRRuntimeHost::GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e962-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="0e962-103"><xref:System.AppDomain>Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="0e962-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e962-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0e962-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e962-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e962-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="0e962-106">dışı <xref:System.AppDomain>Şu anda yürütülmekte olan öğesinin sayısal tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="0e962-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e962-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e962-107">Return Value</span></span>  
  
|<span data-ttu-id="0e962-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e962-108">HRESULT</span></span>|<span data-ttu-id="0e962-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e962-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e962-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e962-110">S_OK</span></span>|<span data-ttu-id="0e962-111">`GetCurrentAppDomainId`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0e962-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="0e962-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e962-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e962-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0e962-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e962-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e962-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e962-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0e962-115">The call timed out.</span></span>|  
|<span data-ttu-id="0e962-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e962-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e962-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0e962-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e962-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e962-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e962-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0e962-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e962-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e962-120">E_FAIL</span></span>|<span data-ttu-id="0e962-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0e962-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e962-122">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0e962-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e962-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e962-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e962-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e962-124">Remarks</span></span>  
 <span data-ttu-id="0e962-125">`pdwAppDomainId`Parametresi <xref:System.AppDomain.Id%2A> , <xref:System.AppDomain> geçerli iş parçacığının yürütüldüğü öğesinin özelliğinin değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0e962-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e962-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e962-126">Requirements</span></span>  
 <span data-ttu-id="0e962-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e962-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e962-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e962-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e962-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0e962-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e962-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e962-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e962-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e962-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="0e962-132">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e962-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)

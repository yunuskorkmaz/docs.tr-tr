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
ms.openlocfilehash: 1b7d321eec2bbc2beb47c5de034bb4ef5d534c9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120463"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="b6433-102">ICLRRuntimeHost::GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6433-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="b6433-103">Şu anda yürütülmekte olan <xref:System.AppDomain> sayısal tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="b6433-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6433-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6433-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6433-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6433-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="b6433-106">dışı Şu anda yürütülmekte olan <xref:System.AppDomain> sayısal tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b6433-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6433-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b6433-107">Return Value</span></span>  
  
|<span data-ttu-id="b6433-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b6433-108">HRESULT</span></span>|<span data-ttu-id="b6433-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b6433-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6433-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b6433-110">S_OK</span></span>|<span data-ttu-id="b6433-111">`GetCurrentAppDomainId` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b6433-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="b6433-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b6433-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b6433-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b6433-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b6433-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b6433-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b6433-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b6433-115">The call timed out.</span></span>|  
|<span data-ttu-id="b6433-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b6433-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b6433-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b6433-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b6433-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b6433-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b6433-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="b6433-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b6433-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="b6433-120">E_FAIL</span></span>|<span data-ttu-id="b6433-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b6433-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b6433-122">Bir yöntem E_FAıL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b6433-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b6433-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6433-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6433-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6433-124">Remarks</span></span>  
 <span data-ttu-id="b6433-125">`pdwAppDomainId` parametresi, geçerli iş parçacığının yürütüldüğü <xref:System.AppDomain> <xref:System.AppDomain.Id%2A> özelliğinin değerine ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b6433-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6433-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6433-126">Requirements</span></span>  
 <span data-ttu-id="b6433-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6433-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6433-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b6433-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b6433-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b6433-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6433-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6433-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6433-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6433-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="b6433-132">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6433-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)

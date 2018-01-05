---
title: ICorRuntimeHost::GetDefaultDomain Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetDefaultDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa732462fb574f1d55fda12f82d8f97da2654e02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="db0b3-102">ICorRuntimeHost::GetDefaultDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="db0b3-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="db0b3-103">Arabirim işaretçisi türü alır <xref:System._AppDomain?displayProperty=nameWithType> , geçerli işlem için varsayılan etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="db0b3-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db0b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db0b3-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db0b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db0b3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="db0b3-106">[out] Arabirim işaretçisi türü <xref:System._AppDomain?displayProperty=nameWithType> için <xref:System.AppDomain> işlemi için varsayılan uygulama etki alanını temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="db0b3-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="db0b3-107">Bu işaretçinin yazılan `IUnknown`, arayanlar genellikle çağırmalıdır `QueryInterface` türünde bir arabirim işaretçisi almak için <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="db0b3-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db0b3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="db0b3-108">Return Value</span></span>  
  
|<span data-ttu-id="db0b3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db0b3-109">HRESULT</span></span>|<span data-ttu-id="db0b3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db0b3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db0b3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="db0b3-111">S_OK</span></span>|<span data-ttu-id="db0b3-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="db0b3-112">The operation was successful.</span></span>|  
|<span data-ttu-id="db0b3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="db0b3-113">S_FALSE</span></span>|<span data-ttu-id="db0b3-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="db0b3-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="db0b3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db0b3-115">E_FAIL</span></span>|<span data-ttu-id="db0b3-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="db0b3-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="db0b3-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="db0b3-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="db0b3-118">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="db0b3-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="db0b3-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="db0b3-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="db0b3-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="db0b3-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db0b3-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db0b3-121">Requirements</span></span>  
 <span data-ttu-id="db0b3-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db0b3-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db0b3-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db0b3-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db0b3-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="db0b3-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db0b3-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="db0b3-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0b3-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db0b3-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="db0b3-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db0b3-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

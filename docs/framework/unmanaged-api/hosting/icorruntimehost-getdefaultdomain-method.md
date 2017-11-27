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
ms.openlocfilehash: 4c482247a0a227c202bb81db09d13ad9af71e60f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="23678-102">ICorRuntimeHost::GetDefaultDomain Metodu</span><span class="sxs-lookup"><span data-stu-id="23678-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="23678-103">Arabirim işaretçisi türü alır <xref:System._AppDomain?displayProperty=nameWithType> , geçerli işlem için varsayılan etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="23678-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23678-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23678-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23678-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23678-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="23678-106">[out] Arabirim işaretçisi türü <xref:System._AppDomain?displayProperty=nameWithType> için <xref:System.AppDomain> işlemi için varsayılan uygulama etki alanını temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="23678-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="23678-107">Bu işaretçinin yazılan `IUnknown`, arayanlar genellikle çağırmalıdır `QueryInterface` türünde bir arabirim işaretçisi almak için <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="23678-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23678-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23678-108">Return Value</span></span>  
  
|<span data-ttu-id="23678-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23678-109">HRESULT</span></span>|<span data-ttu-id="23678-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23678-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23678-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="23678-111">S_OK</span></span>|<span data-ttu-id="23678-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="23678-112">The operation was successful.</span></span>|  
|<span data-ttu-id="23678-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="23678-113">S_FALSE</span></span>|<span data-ttu-id="23678-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="23678-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="23678-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="23678-115">E_FAIL</span></span>|<span data-ttu-id="23678-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="23678-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="23678-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="23678-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="23678-118">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="23678-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="23678-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="23678-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="23678-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="23678-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23678-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23678-121">Requirements</span></span>  
 <span data-ttu-id="23678-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23678-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23678-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="23678-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23678-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="23678-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23678-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="23678-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23678-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23678-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="23678-127">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="23678-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

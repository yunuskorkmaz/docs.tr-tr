---
title: "ICorRuntimeHost::CurrentDomain Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CurrentDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 592b604f5e873f479f2e0489144240c3f021c270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="73e50-102">ICorRuntimeHost::CurrentDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73e50-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="73e50-103">Arabirim işaretçisi türü alır <xref:System.AppDomain?displayProperty=nameWithType> geçerli iş parçacığı üzerinde yüklenen etki alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73e50-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73e50-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73e50-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73e50-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="73e50-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="73e50-106">[out] Bir işaretçi türü <xref:System.AppDomain?displayProperty=nameWithType> , iş parçacığının geçerli uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73e50-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="73e50-107">Bu işaretçinin yazılan `IUnknown`, arayanlar genellikle çağırmalıdır `QueryInterface` bir işaretçi türü almak için <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="73e50-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73e50-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="73e50-108">Return Value</span></span>  
  
|<span data-ttu-id="73e50-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73e50-109">HRESULT</span></span>|<span data-ttu-id="73e50-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73e50-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73e50-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="73e50-111">S_OK</span></span>|<span data-ttu-id="73e50-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="73e50-112">The operation was successful.</span></span>|  
|<span data-ttu-id="73e50-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="73e50-113">S_FALSE</span></span>|<span data-ttu-id="73e50-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="73e50-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="73e50-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73e50-115">E_FAIL</span></span>|<span data-ttu-id="73e50-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="73e50-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="73e50-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="73e50-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="73e50-118">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="73e50-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="73e50-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="73e50-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="73e50-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="73e50-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73e50-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73e50-121">Requirements</span></span>  
 <span data-ttu-id="73e50-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73e50-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e50-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73e50-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73e50-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="73e50-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73e50-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="73e50-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e50-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73e50-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="73e50-127">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="73e50-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

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
ms.workload: dotnet
ms.openlocfilehash: 1ac437d924b6f5b290db117260701b554e29b6e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="1474a-102">ICorRuntimeHost::CurrentDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1474a-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="1474a-103">Arabirim işaretçisi türü alır <xref:System.AppDomain?displayProperty=nameWithType> geçerli iş parçacığı üzerinde yüklenen etki alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1474a-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1474a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1474a-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1474a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1474a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1474a-106">[out] Bir işaretçi türü <xref:System.AppDomain?displayProperty=nameWithType> , iş parçacığının geçerli uygulama etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1474a-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="1474a-107">Bu işaretçinin yazılan `IUnknown`, arayanlar genellikle çağırmalıdır `QueryInterface` bir işaretçi türü almak için <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1474a-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1474a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1474a-108">Return Value</span></span>  
  
|<span data-ttu-id="1474a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1474a-109">HRESULT</span></span>|<span data-ttu-id="1474a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1474a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1474a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1474a-111">S_OK</span></span>|<span data-ttu-id="1474a-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="1474a-112">The operation was successful.</span></span>|  
|<span data-ttu-id="1474a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1474a-113">S_FALSE</span></span>|<span data-ttu-id="1474a-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="1474a-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1474a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1474a-115">E_FAIL</span></span>|<span data-ttu-id="1474a-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1474a-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1474a-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1474a-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1474a-118">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1474a-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1474a-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1474a-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1474a-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1474a-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1474a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1474a-121">Requirements</span></span>  
 <span data-ttu-id="1474a-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1474a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1474a-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1474a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1474a-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1474a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1474a-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1474a-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1474a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1474a-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="1474a-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1474a-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

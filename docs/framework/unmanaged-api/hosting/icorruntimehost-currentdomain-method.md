---
title: ICorRuntimeHost::CurrentDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0230f2e313b6d84b2c249afb28f7c5fdf34fdd0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479668"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="9de09-102">ICorRuntimeHost::CurrentDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9de09-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="9de09-103">Türü bir arabirim işaretçisi alır <xref:System.AppDomain?displayProperty=nameWithType> geçerli iş parçacığı üzerinde yüklü etki alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9de09-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9de09-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9de09-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9de09-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9de09-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9de09-106">[out] Türünde bir işaretçi <xref:System.AppDomain?displayProperty=nameWithType> temsil eden iş parçacığının geçerli uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="9de09-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="9de09-107">Bu işaretçinin türü belirtilmiş `IUnknown`, Arayanların genellikle çağırmalıdır `QueryInterface` türünde bir işaretçi edinme <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9de09-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9de09-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9de09-108">Return Value</span></span>  
  
|<span data-ttu-id="9de09-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9de09-109">HRESULT</span></span>|<span data-ttu-id="9de09-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9de09-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9de09-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9de09-111">S_OK</span></span>|<span data-ttu-id="9de09-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="9de09-112">The operation was successful.</span></span>|  
|<span data-ttu-id="9de09-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9de09-113">S_FALSE</span></span>|<span data-ttu-id="9de09-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="9de09-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9de09-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9de09-115">E_FAIL</span></span>|<span data-ttu-id="9de09-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9de09-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9de09-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9de09-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9de09-118">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9de09-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9de09-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9de09-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9de09-120">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9de09-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9de09-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9de09-121">Requirements</span></span>  
 <span data-ttu-id="9de09-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9de09-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9de09-123">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9de09-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9de09-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9de09-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9de09-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9de09-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de09-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9de09-126">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="9de09-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9de09-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

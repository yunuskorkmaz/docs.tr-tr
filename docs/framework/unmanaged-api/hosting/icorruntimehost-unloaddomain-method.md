---
title: "ICorRuntimeHost::UnloadDomain Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 067b60b9da02300e9e7316712d0058a61ab8a697
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="ae278-102">ICorRuntimeHost::UnloadDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae278-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="ae278-103">Belirtilen uygulama etki alanından geçerli işlem kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ae278-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae278-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae278-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae278-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae278-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ae278-106">[in] Bir işaretçi türü <xref:System._AppDomain?displayProperty=nameWithType> boşaltılması için etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ae278-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae278-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae278-107">Return Value</span></span>  
  
|<span data-ttu-id="ae278-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae278-108">HRESULT</span></span>|<span data-ttu-id="ae278-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae278-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae278-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae278-110">S_OK</span></span>|<span data-ttu-id="ae278-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="ae278-111">The operation was successful.</span></span>|  
|<span data-ttu-id="ae278-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ae278-112">S_FALSE</span></span>|<span data-ttu-id="ae278-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="ae278-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ae278-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae278-114">E_FAIL</span></span>|<span data-ttu-id="ae278-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ae278-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ae278-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ae278-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ae278-117">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae278-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ae278-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ae278-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ae278-119">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ae278-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae278-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae278-120">Requirements</span></span>  
 <span data-ttu-id="ae278-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae278-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae278-122">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae278-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae278-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ae278-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae278-124">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ae278-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae278-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae278-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="ae278-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae278-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

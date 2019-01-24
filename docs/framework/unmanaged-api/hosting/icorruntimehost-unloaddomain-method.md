---
title: ICorRuntimeHost::UnloadDomain Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d769c54c67e146df3dbe00f3a7aedad43ba548a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528699"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="a9987-102">ICorRuntimeHost::UnloadDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9987-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="a9987-103">Belirtilen uygulama etki alanından geçerli işlem kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a9987-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9987-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9987-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9987-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9987-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a9987-106">[in] Türünde bir işaretçi <xref:System._AppDomain?displayProperty=nameWithType> kaldırılacak etki alanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a9987-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9987-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9987-107">Return Value</span></span>  
  
|<span data-ttu-id="a9987-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9987-108">HRESULT</span></span>|<span data-ttu-id="a9987-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9987-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9987-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9987-110">S_OK</span></span>|<span data-ttu-id="a9987-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="a9987-111">The operation was successful.</span></span>|  
|<span data-ttu-id="a9987-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a9987-112">S_FALSE</span></span>|<span data-ttu-id="a9987-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="a9987-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a9987-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a9987-114">E_FAIL</span></span>|<span data-ttu-id="a9987-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a9987-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a9987-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a9987-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a9987-117">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9987-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a9987-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a9987-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a9987-119">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a9987-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9987-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9987-120">Requirements</span></span>  
 <span data-ttu-id="a9987-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9987-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9987-122">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a9987-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a9987-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a9987-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9987-124">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a9987-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9987-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9987-125">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="a9987-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9987-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

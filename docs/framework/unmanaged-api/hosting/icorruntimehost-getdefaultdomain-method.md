---
title: ICorRuntimeHost::GetDefaultDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41a6c5ee73cad77368e83792d11d455d8fb163fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106177"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="a3d3e-102">ICorRuntimeHost::GetDefaultDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3d3e-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="a3d3e-103">Türü bir arabirim işaretçisi alır <xref:System._AppDomain?displayProperty=nameWithType> , geçerli işlem için varsayılan etki alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3d3e-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3d3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3d3e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a3d3e-106">[out] Bir arabirim işaretçisi türünde <xref:System._AppDomain?displayProperty=nameWithType> için <xref:System.AppDomain> işlem için varsayılan uygulama etki alanı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="a3d3e-107">Bu işaretçinin türü belirtilmiş `IUnknown`, Arayanların genellikle çağırmalıdır `QueryInterface` bir arabirim işaretçisi türü elde etmek için <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3d3e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a3d3e-108">Return Value</span></span>  
  
|<span data-ttu-id="a3d3e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3d3e-109">HRESULT</span></span>|<span data-ttu-id="a3d3e-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3d3e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3d3e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3d3e-111">S_OK</span></span>|<span data-ttu-id="a3d3e-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-112">The operation was successful.</span></span>|  
|<span data-ttu-id="a3d3e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a3d3e-113">S_FALSE</span></span>|<span data-ttu-id="a3d3e-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a3d3e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3d3e-115">E_FAIL</span></span>|<span data-ttu-id="a3d3e-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a3d3e-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a3d3e-118">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a3d3e-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a3d3e-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a3d3e-120">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3d3e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3d3e-121">Requirements</span></span>  
 <span data-ttu-id="a3d3e-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3d3e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3d3e-123">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3d3e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3d3e-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a3d3e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3d3e-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a3d3e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d3e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3d3e-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="a3d3e-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3d3e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

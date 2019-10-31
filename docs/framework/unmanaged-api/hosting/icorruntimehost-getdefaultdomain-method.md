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
ms.openlocfilehash: 6dc25cbeef2576a2ecc6ec39b2cb3f9abb7b9964
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139560"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="69bf1-102">ICorRuntimeHost::GetDefaultDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69bf1-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="69bf1-103">Geçerli işlem için varsayılan etki alanını temsil eden <xref:System._AppDomain?displayProperty=nameWithType> türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="69bf1-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69bf1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69bf1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69bf1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69bf1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="69bf1-106">dışı İşlem için varsayılan uygulama etki alanını temsil eden <xref:System.AppDomain> örneğine <xref:System._AppDomain?displayProperty=nameWithType> türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="69bf1-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="69bf1-107">Bu işaretçi `IUnknown`yazılır, bu nedenle çağıranlar genellikle <xref:System._AppDomain?displayProperty=nameWithType>türünde bir arabirim işaretçisi almak için `QueryInterface` çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="69bf1-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69bf1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69bf1-108">Return Value</span></span>  
  
|<span data-ttu-id="69bf1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="69bf1-109">HRESULT</span></span>|<span data-ttu-id="69bf1-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69bf1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69bf1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="69bf1-111">S_OK</span></span>|<span data-ttu-id="69bf1-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="69bf1-112">The operation was successful.</span></span>|  
|<span data-ttu-id="69bf1-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="69bf1-113">S_FALSE</span></span>|<span data-ttu-id="69bf1-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="69bf1-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="69bf1-115">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="69bf1-115">E_FAIL</span></span>|<span data-ttu-id="69bf1-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="69bf1-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="69bf1-117">Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="69bf1-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="69bf1-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="69bf1-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="69bf1-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="69bf1-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="69bf1-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="69bf1-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69bf1-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69bf1-121">Requirements</span></span>  
 <span data-ttu-id="69bf1-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69bf1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69bf1-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="69bf1-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69bf1-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="69bf1-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69bf1-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="69bf1-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69bf1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69bf1-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="69bf1-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69bf1-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

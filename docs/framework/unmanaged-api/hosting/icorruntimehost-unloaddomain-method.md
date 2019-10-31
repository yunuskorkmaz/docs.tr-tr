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
ms.openlocfilehash: dfdcb9b8aedeb3ccbbd27864e79ce43338942922
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133351"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="ed61a-102">ICorRuntimeHost::UnloadDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed61a-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="ed61a-103">Belirtilen uygulama etki alanını geçerli işlemden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="ed61a-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed61a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed61a-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed61a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed61a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ed61a-106">'ndaki Kaldırılacak etki alanını temsil eden <xref:System._AppDomain?displayProperty=nameWithType> türünde bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ed61a-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed61a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ed61a-107">Return Value</span></span>  
  
|<span data-ttu-id="ed61a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ed61a-108">HRESULT</span></span>|<span data-ttu-id="ed61a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed61a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ed61a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed61a-110">S_OK</span></span>|<span data-ttu-id="ed61a-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="ed61a-111">The operation was successful.</span></span>|  
|<span data-ttu-id="ed61a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ed61a-112">S_FALSE</span></span>|<span data-ttu-id="ed61a-113">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="ed61a-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ed61a-114">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="ed61a-114">E_FAIL</span></span>|<span data-ttu-id="ed61a-115">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ed61a-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ed61a-116">Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ed61a-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ed61a-117">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ed61a-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ed61a-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ed61a-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ed61a-119">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ed61a-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed61a-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed61a-120">Requirements</span></span>  
 <span data-ttu-id="ed61a-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed61a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed61a-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ed61a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed61a-123">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ed61a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed61a-124">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="ed61a-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed61a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed61a-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="ed61a-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed61a-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

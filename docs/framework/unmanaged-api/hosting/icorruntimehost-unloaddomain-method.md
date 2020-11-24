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
ms.openlocfilehash: 94c84d876e19ec2ff7baba5a5a7420eec68d58c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690115"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="1e8e8-102">ICorRuntimeHost::UnloadDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e8e8-102">ICorRuntimeHost::UnloadDomain Method</span></span>

<span data-ttu-id="1e8e8-103">Belirtilen uygulama etki alanını geçerli işlemden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e8e8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1e8e8-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e8e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e8e8-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="1e8e8-106">'ndaki <xref:System._AppDomain?displayProperty=nameWithType> Kaldırılacak etki alanını temsil eden tür işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e8e8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1e8e8-107">Return Value</span></span>  
  
|<span data-ttu-id="1e8e8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1e8e8-108">HRESULT</span></span>|<span data-ttu-id="1e8e8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e8e8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e8e8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1e8e8-110">S_OK</span></span>|<span data-ttu-id="1e8e8-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-111">The operation was successful.</span></span>|  
|<span data-ttu-id="1e8e8-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1e8e8-112">S_FALSE</span></span>|<span data-ttu-id="1e8e8-113">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1e8e8-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1e8e8-114">E_FAIL</span></span>|<span data-ttu-id="1e8e8-115">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1e8e8-116">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1e8e8-117">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1e8e8-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1e8e8-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1e8e8-119">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1e8e8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e8e8-120">Requirements</span></span>  

 <span data-ttu-id="1e8e8-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e8e8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e8e8-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1e8e8-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e8e8-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1e8e8-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e8e8-124">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1e8e8-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e8e8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e8e8-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="1e8e8-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e8e8-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

---
description: ': ICorRuntimeHost:: UnloadDomain metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b191f2342778b2f2ed7ddb7b1fb548c73be96599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799403"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="e9f9b-103">ICorRuntimeHost::UnloadDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9f9b-103">ICorRuntimeHost::UnloadDomain Method</span></span>

<span data-ttu-id="e9f9b-104">Belirtilen uygulama etki alanını geçerli işlemden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-104">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9f9b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9f9b-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9f9b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9f9b-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="e9f9b-107">'ndaki <xref:System._AppDomain?displayProperty=nameWithType> Kaldırılacak etki alanını temsil eden tür işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-107">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9f9b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9f9b-108">Return Value</span></span>  
  
|<span data-ttu-id="e9f9b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9f9b-109">HRESULT</span></span>|<span data-ttu-id="e9f9b-110">Description</span><span class="sxs-lookup"><span data-stu-id="e9f9b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9f9b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9f9b-111">S_OK</span></span>|<span data-ttu-id="e9f9b-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-112">The operation was successful.</span></span>|  
|<span data-ttu-id="e9f9b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e9f9b-113">S_FALSE</span></span>|<span data-ttu-id="e9f9b-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e9f9b-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9f9b-115">E_FAIL</span></span>|<span data-ttu-id="e9f9b-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e9f9b-117">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e9f9b-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e9f9b-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9f9b-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9f9b-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9f9b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9f9b-121">Requirements</span></span>  

 <span data-ttu-id="e9f9b-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9f9b-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9f9b-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e9f9b-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9f9b-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e9f9b-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9f9b-125">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="e9f9b-125">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f9b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9f9b-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e9f9b-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9f9b-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

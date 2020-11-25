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
ms.openlocfilehash: 673c32c86c808c36db6454b8a9f0d8e68f9b1258
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720639"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="fb5b6-102">ICorRuntimeHost::GetDefaultDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb5b6-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>

<span data-ttu-id="fb5b6-103"><xref:System._AppDomain?displayProperty=nameWithType>Geçerli işlem için varsayılan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb5b6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fb5b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb5b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb5b6-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="fb5b6-106">dışı <xref:System._AppDomain?displayProperty=nameWithType> <xref:System.AppDomain> İşlemin varsayılan uygulama etki alanını temsil eden örneğe türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="fb5b6-107">Bu işaretçi yazıldığı `IUnknown` için, arayanların genellikle `QueryInterface` türünde bir arabirim işaretçisi almak için çağrı yapmaları gerekir <xref:System._AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fb5b6-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb5b6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fb5b6-108">Return Value</span></span>  
  
|<span data-ttu-id="fb5b6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fb5b6-109">HRESULT</span></span>|<span data-ttu-id="fb5b6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb5b6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb5b6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fb5b6-111">S_OK</span></span>|<span data-ttu-id="fb5b6-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-112">The operation was successful.</span></span>|  
|<span data-ttu-id="fb5b6-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fb5b6-113">S_FALSE</span></span>|<span data-ttu-id="fb5b6-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="fb5b6-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fb5b6-115">E_FAIL</span></span>|<span data-ttu-id="fb5b6-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="fb5b6-117">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="fb5b6-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fb5b6-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fb5b6-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fb5b6-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fb5b6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb5b6-121">Requirements</span></span>  

 <span data-ttu-id="fb5b6-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb5b6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb5b6-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fb5b6-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb5b6-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fb5b6-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb5b6-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="fb5b6-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb5b6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb5b6-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="fb5b6-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb5b6-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

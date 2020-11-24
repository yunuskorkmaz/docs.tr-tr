---
title: ICorRuntimeHost::NextDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: 598c46d50d7b4a67c1b2c0d844c9b12deb12a428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671375"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="f2b1d-102">ICorRuntimeHost::NextDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2b1d-102">ICorRuntimeHost::NextDomain Method</span></span>

<span data-ttu-id="f2b1d-103">Numaralandırmadaki bir sonraki etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b1d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f2b1d-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2b1d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2b1d-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="f2b1d-106">'ndaki [EnumDomains](icorruntimehost-enumdomains-method.md)çağrısıyla edinilen Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-106">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="f2b1d-107">dışı <xref:System._AppDomain?displayProperty=nameWithType> Numaradaki bir sonraki etki alanını temsil eden tür için bir arabirim işaretçisi veya daha fazla etki alanı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2b1d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f2b1d-108">Return Value</span></span>  
  
|<span data-ttu-id="f2b1d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f2b1d-109">HRESULT</span></span>|<span data-ttu-id="f2b1d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2b1d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f2b1d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f2b1d-111">S_OK</span></span>|<span data-ttu-id="f2b1d-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-112">The operation was successful.</span></span>|  
|<span data-ttu-id="f2b1d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="f2b1d-113">S_FALSE</span></span>|<span data-ttu-id="f2b1d-114">İşlem tamamlanamadı veya numaralandırmada başka etki alanı yok.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="f2b1d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f2b1d-115">E_FAIL</span></span>|<span data-ttu-id="f2b1d-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="f2b1d-117">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="f2b1d-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f2b1d-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f2b1d-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f2b1d-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2b1d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2b1d-121">Requirements</span></span>  

 <span data-ttu-id="f2b1d-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b1d-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b1d-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f2b1d-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f2b1d-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f2b1d-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f2b1d-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="f2b1d-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b1d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2b1d-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="f2b1d-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2b1d-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

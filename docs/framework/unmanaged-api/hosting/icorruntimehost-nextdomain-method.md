---
description: ': ICorRuntimeHost:: NextDomain Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cfced9d1d3c91f4ec9508b86157ceebae9f95a56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789625"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="30b4c-103">ICorRuntimeHost::NextDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30b4c-103">ICorRuntimeHost::NextDomain Method</span></span>

<span data-ttu-id="30b4c-104">Numaralandırmadaki bir sonraki etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="30b4c-104">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b4c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30b4c-105">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30b4c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30b4c-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="30b4c-107">'ndaki [EnumDomains](icorruntimehost-enumdomains-method.md)çağrısıyla edinilen Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="30b4c-107">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="30b4c-108">dışı <xref:System._AppDomain?displayProperty=nameWithType> Numaradaki bir sonraki etki alanını temsil eden tür için bir arabirim işaretçisi veya daha fazla etki alanı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="30b4c-108">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30b4c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30b4c-109">Return Value</span></span>  
  
|<span data-ttu-id="30b4c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30b4c-110">HRESULT</span></span>|<span data-ttu-id="30b4c-111">Description</span><span class="sxs-lookup"><span data-stu-id="30b4c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30b4c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="30b4c-112">S_OK</span></span>|<span data-ttu-id="30b4c-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="30b4c-113">The operation was successful.</span></span>|  
|<span data-ttu-id="30b4c-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="30b4c-114">S_FALSE</span></span>|<span data-ttu-id="30b4c-115">İşlem tamamlanamadı veya numaralandırmada başka etki alanı yok.</span><span class="sxs-lookup"><span data-stu-id="30b4c-115">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="30b4c-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30b4c-116">E_FAIL</span></span>|<span data-ttu-id="30b4c-117">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="30b4c-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="30b4c-118">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="30b4c-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="30b4c-119">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="30b4c-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="30b4c-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30b4c-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30b4c-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="30b4c-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30b4c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30b4c-122">Requirements</span></span>  

 <span data-ttu-id="30b4c-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30b4c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30b4c-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30b4c-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30b4c-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="30b4c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30b4c-126">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="30b4c-126">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30b4c-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30b4c-127">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="30b4c-128">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30b4c-128">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

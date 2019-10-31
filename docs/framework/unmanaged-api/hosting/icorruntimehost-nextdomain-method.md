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
ms.openlocfilehash: 36eacedfb83c1248fc252091872bcfeecdbcd874
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139501"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="37836-102">ICorRuntimeHost::NextDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37836-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="37836-103">Numaralandırmadaki bir sonraki etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="37836-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37836-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37836-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37836-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="37836-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="37836-106">'ndaki [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)çağrısıyla edinilen Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="37836-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="37836-107">dışı Numaralandırmadaki bir sonraki etki alanını temsil eden <xref:System._AppDomain?displayProperty=nameWithType> türüne yönelik bir arabirim işaretçisi veya daha fazla etki alanı yoksa null.</span><span class="sxs-lookup"><span data-stu-id="37836-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37836-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="37836-108">Return Value</span></span>  
  
|<span data-ttu-id="37836-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37836-109">HRESULT</span></span>|<span data-ttu-id="37836-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37836-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37836-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="37836-111">S_OK</span></span>|<span data-ttu-id="37836-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="37836-112">The operation was successful.</span></span>|  
|<span data-ttu-id="37836-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="37836-113">S_FALSE</span></span>|<span data-ttu-id="37836-114">İşlem tamamlanamadı veya numaralandırmada başka etki alanı yok.</span><span class="sxs-lookup"><span data-stu-id="37836-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="37836-115">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="37836-115">E_FAIL</span></span>|<span data-ttu-id="37836-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="37836-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="37836-117">Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="37836-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="37836-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="37836-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="37836-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37836-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37836-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="37836-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37836-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37836-121">Requirements</span></span>  
 <span data-ttu-id="37836-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37836-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37836-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="37836-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37836-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="37836-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37836-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="37836-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37836-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37836-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="37836-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37836-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

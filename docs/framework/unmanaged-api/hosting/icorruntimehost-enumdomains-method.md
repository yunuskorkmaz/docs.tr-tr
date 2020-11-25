---
title: ICorRuntimeHost::EnumDomains Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
ms.openlocfilehash: f4338429dc24bf5196b92d3f18e73c98442f61e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720668"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="bc71a-102">ICorRuntimeHost::EnumDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bc71a-102">ICorRuntimeHost::EnumDomains Method</span></span>

<span data-ttu-id="bc71a-103">Geçerli işlemdeki etki alanları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="bc71a-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc71a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bc71a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc71a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bc71a-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="bc71a-106">dışı Etki alanları için bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="bc71a-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc71a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bc71a-107">Return Value</span></span>  
  
|<span data-ttu-id="bc71a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bc71a-108">HRESULT</span></span>|<span data-ttu-id="bc71a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc71a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc71a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc71a-110">S_OK</span></span>|<span data-ttu-id="bc71a-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="bc71a-111">The operation was successful.</span></span>|  
|<span data-ttu-id="bc71a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bc71a-112">S_FALSE</span></span>|<span data-ttu-id="bc71a-113">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="bc71a-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="bc71a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bc71a-114">E_FAIL</span></span>|<span data-ttu-id="bc71a-115">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bc71a-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="bc71a-116">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bc71a-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="bc71a-117">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc71a-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bc71a-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bc71a-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bc71a-119">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bc71a-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc71a-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc71a-120">Requirements</span></span>  

 <span data-ttu-id="bc71a-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc71a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc71a-122">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bc71a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc71a-123">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bc71a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc71a-124">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="bc71a-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc71a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc71a-125">See also</span></span>

- [<span data-ttu-id="bc71a-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc71a-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

---
description: ': ICorRuntimeHost:: EnumDomains yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e581fe95a78a4f55d50a99e4925e03a1777268a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784879"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="22353-103">ICorRuntimeHost::EnumDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="22353-103">ICorRuntimeHost::EnumDomains Method</span></span>

<span data-ttu-id="22353-104">Geçerli işlemdeki etki alanları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="22353-104">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22353-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22353-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22353-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="22353-106">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="22353-107">dışı Etki alanları için bir Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="22353-107">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22353-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="22353-108">Return Value</span></span>  
  
|<span data-ttu-id="22353-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22353-109">HRESULT</span></span>|<span data-ttu-id="22353-110">Description</span><span class="sxs-lookup"><span data-stu-id="22353-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22353-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="22353-111">S_OK</span></span>|<span data-ttu-id="22353-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="22353-112">The operation was successful.</span></span>|  
|<span data-ttu-id="22353-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="22353-113">S_FALSE</span></span>|<span data-ttu-id="22353-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="22353-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="22353-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22353-115">E_FAIL</span></span>|<span data-ttu-id="22353-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="22353-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="22353-117">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="22353-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="22353-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="22353-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="22353-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22353-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22353-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="22353-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22353-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="22353-121">Requirements</span></span>  

 <span data-ttu-id="22353-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22353-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22353-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="22353-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22353-124">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="22353-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22353-125">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="22353-125">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22353-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22353-126">See also</span></span>

- [<span data-ttu-id="22353-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="22353-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

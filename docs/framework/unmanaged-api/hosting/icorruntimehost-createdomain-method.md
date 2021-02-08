---
description: ': ICorRuntimeHost:: CreateDomain yöntemi hakkında daha fazla bilgi edinin'
title: ICorRuntimeHost::CreateDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
ms.openlocfilehash: 6173d74d97ddb9dec619db8583036ec763a9e293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789716"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="c39a4-103">ICorRuntimeHost::CreateDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c39a4-103">ICorRuntimeHost::CreateDomain Method</span></span>

<span data-ttu-id="c39a4-104">Bir uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c39a4-104">Creates an application domain.</span></span> <span data-ttu-id="c39a4-105">Çağıran, türünde bir örneğine türünde bir arabirim işaretçisi alır <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c39a4-105">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c39a4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c39a4-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c39a4-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c39a4-107">Parameters</span></span>  

 `pwzFriendlyName`  
 <span data-ttu-id="c39a4-108">'ndaki Etki alanına kolay bir ad vermek için kullanılan isteğe bağlı bir parametre.</span><span class="sxs-lookup"><span data-stu-id="c39a4-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="c39a4-109">Bu kolay ad, etki alanını tanımlamak için hata ayıklayıcılar gibi kullanıcı arabirimlerinde gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="c39a4-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="c39a4-110">'ndaki `IIdentity` Bir izin kümesi oluşturmak için güvenlik ilkesiyle eşlenen kanıtları temsil eden örneklere yönelik işaretçilerin bir dizisi.</span><span class="sxs-lookup"><span data-stu-id="c39a4-110">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="c39a4-111">Bir `IIdentity` nesnesi [createkanıt](icorruntimehost-createevidence-method.md) yöntemi çağırarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c39a4-111">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="c39a4-112">dışı <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> Etki alanını daha fazla denetlemek için kullanılan bir örneğine türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c39a4-112">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c39a4-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c39a4-113">Return Value</span></span>  
  
|<span data-ttu-id="c39a4-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c39a4-114">HRESULT</span></span>|<span data-ttu-id="c39a4-115">Description</span><span class="sxs-lookup"><span data-stu-id="c39a4-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c39a4-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c39a4-116">S_OK</span></span>|<span data-ttu-id="c39a4-117">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c39a4-117">The operation was successful.</span></span>|  
|<span data-ttu-id="c39a4-118">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c39a4-118">S_FALSE</span></span>|<span data-ttu-id="c39a4-119">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="c39a4-119">The operation failed to complete.</span></span>|  
|<span data-ttu-id="c39a4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c39a4-120">E_FAIL</span></span>|<span data-ttu-id="c39a4-121">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c39a4-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c39a4-122">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c39a4-122">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="c39a4-123">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c39a4-123">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c39a4-124">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c39a4-124">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c39a4-125">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c39a4-125">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c39a4-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c39a4-126">Requirements</span></span>  

 <span data-ttu-id="c39a4-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c39a4-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c39a4-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c39a4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c39a4-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c39a4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c39a4-130">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="c39a4-130">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39a4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c39a4-131">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="c39a4-132">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c39a4-132">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

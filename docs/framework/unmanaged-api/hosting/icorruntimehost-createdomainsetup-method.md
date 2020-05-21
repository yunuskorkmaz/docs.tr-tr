---
title: ICorRuntimeHost::CreateDomainSetup Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: aa1ce70311cd4ef0204c1c31efee8bd7b313c81d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762337"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="a7808-102">ICorRuntimeHost::CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7808-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="a7808-103">Bir örneğe IAppDomainSetup türünde bir arabirim işaretçisi alır <xref:System.AppDomainSetup?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a7808-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="a7808-104">`IAppDomainSetup`, bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7808-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7808-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a7808-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7808-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7808-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="a7808-107">dışı Bir örneğe yönelik arabirim işaretçisi <xref:System.AppDomainSetup?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a7808-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="a7808-108">Bu parametre olarak yazılır `IUnknown` , bu nedenle çağıranlar `QueryInterface` türü bir arabirim işaretçisi almak için genellikle bu işaretçiye çağrı yapmalıdır `IAppDomainSetup` .</span><span class="sxs-lookup"><span data-stu-id="a7808-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7808-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7808-109">Return Value</span></span>  
  
|<span data-ttu-id="a7808-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7808-110">HRESULT</span></span>|<span data-ttu-id="a7808-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a7808-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7808-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7808-112">S_OK</span></span>|<span data-ttu-id="a7808-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="a7808-113">The operation was successful.</span></span>|  
|<span data-ttu-id="a7808-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a7808-114">S_FALSE</span></span>|<span data-ttu-id="a7808-115">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="a7808-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a7808-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7808-116">E_FAIL</span></span>|<span data-ttu-id="a7808-117">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a7808-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a7808-118">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a7808-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a7808-119">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a7808-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a7808-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7808-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7808-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a7808-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7808-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7808-122">Remarks</span></span>  
 <span data-ttu-id="a7808-123">Bu yöntemden döndürülen işaretçi genellikle [CreateDomainEx](icorruntimehost-createdomainex-method.md) metoduna parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="a7808-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7808-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7808-124">Requirements</span></span>  
 <span data-ttu-id="a7808-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7808-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7808-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a7808-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7808-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a7808-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7808-128">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="a7808-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7808-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7808-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="a7808-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7808-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

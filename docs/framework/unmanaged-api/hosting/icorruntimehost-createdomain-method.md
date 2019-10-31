---
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
ms.openlocfilehash: 7c3e37fdb8a5afc973c913b1cfa56ab2e9f4fa52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127725"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="622ef-102">ICorRuntimeHost::CreateDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="622ef-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="622ef-103">Bir uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="622ef-103">Creates an application domain.</span></span> <span data-ttu-id="622ef-104">Çağıran, <xref:System.AppDomain?displayProperty=nameWithType>türünde bir örneğe <xref:System._AppDomain> türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="622ef-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="622ef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="622ef-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="622ef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="622ef-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="622ef-107">'ndaki Etki alanına kolay bir ad vermek için kullanılan isteğe bağlı bir parametre.</span><span class="sxs-lookup"><span data-stu-id="622ef-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="622ef-108">Bu kolay ad, etki alanını tanımlamak için hata ayıklayıcılar gibi kullanıcı arabirimlerinde gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="622ef-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="622ef-109">'ndaki Bir izin kümesi oluşturmak için güvenlik ilkesiyle eşlenen kanıtları temsil eden `IIdentity` örneklerine yönelik bir işaretçi dizisi.</span><span class="sxs-lookup"><span data-stu-id="622ef-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="622ef-110">`IIdentity` nesnesi [Createkanıt](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) yöntemi çağırarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="622ef-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="622ef-111">dışı Etki alanını daha fazla denetlemek için kullanılabilecek bir <xref:System.AppDomain?displayProperty=nameWithType> örneğine <xref:System._AppDomain> türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="622ef-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="622ef-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="622ef-112">Return Value</span></span>  
  
|<span data-ttu-id="622ef-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="622ef-113">HRESULT</span></span>|<span data-ttu-id="622ef-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="622ef-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="622ef-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="622ef-115">S_OK</span></span>|<span data-ttu-id="622ef-116">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="622ef-116">The operation was successful.</span></span>|  
|<span data-ttu-id="622ef-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="622ef-117">S_FALSE</span></span>|<span data-ttu-id="622ef-118">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="622ef-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="622ef-119">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="622ef-119">E_FAIL</span></span>|<span data-ttu-id="622ef-120">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="622ef-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="622ef-121">Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="622ef-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="622ef-122">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="622ef-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="622ef-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="622ef-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="622ef-124">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="622ef-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="622ef-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="622ef-125">Requirements</span></span>  
 <span data-ttu-id="622ef-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="622ef-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="622ef-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="622ef-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="622ef-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="622ef-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="622ef-129">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="622ef-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622ef-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="622ef-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="622ef-131">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="622ef-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)

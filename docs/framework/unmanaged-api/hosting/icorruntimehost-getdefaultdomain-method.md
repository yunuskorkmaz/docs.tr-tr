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
ms.openlocfilehash: a23083777d0cd5965511f3689578a60220008420
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762236"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="19261-102">ICorRuntimeHost::GetDefaultDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19261-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="19261-103"><xref:System._AppDomain?displayProperty=nameWithType>Geçerli işlem için varsayılan etki alanını temsil eden türün bir arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="19261-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19261-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="19261-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19261-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="19261-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="19261-106">dışı <xref:System._AppDomain?displayProperty=nameWithType> <xref:System.AppDomain> İşlemin varsayılan uygulama etki alanını temsil eden örneğe türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="19261-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="19261-107">Bu işaretçi yazıldığı `IUnknown` için, arayanların genellikle `QueryInterface` türünde bir arabirim işaretçisi almak için çağrı yapmaları gerekir <xref:System._AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="19261-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19261-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="19261-108">Return Value</span></span>  
  
|<span data-ttu-id="19261-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19261-109">HRESULT</span></span>|<span data-ttu-id="19261-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19261-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19261-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="19261-111">S_OK</span></span>|<span data-ttu-id="19261-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="19261-112">The operation was successful.</span></span>|  
|<span data-ttu-id="19261-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="19261-113">S_FALSE</span></span>|<span data-ttu-id="19261-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="19261-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="19261-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19261-115">E_FAIL</span></span>|<span data-ttu-id="19261-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="19261-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="19261-117">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="19261-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="19261-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="19261-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="19261-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19261-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19261-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="19261-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19261-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19261-121">Requirements</span></span>  
 <span data-ttu-id="19261-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19261-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19261-123">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="19261-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19261-124">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="19261-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19261-125">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="19261-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19261-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19261-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="19261-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19261-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)

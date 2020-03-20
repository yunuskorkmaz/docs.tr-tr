---
title: ClrCreateManagedInstance İşlevi
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176545"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="cf86e-102">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="cf86e-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="cf86e-103">Belirtilen yönetilen türbir örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf86e-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="cf86e-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cf86e-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="cf86e-105">Yönetilen türün bir örneğini oluşturmak veya barındırma kullanmak için COM etkinleştirme sini kullanın (bkz. [.NET Framework 4 ve 4.5'te eklenen CLR Barındırma Arabirimleri).](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)</span><span class="sxs-lookup"><span data-stu-id="cf86e-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf86e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf86e-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf86e-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf86e-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="cf86e-108">[içinde] İstenilen örnek türü adına bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf86e-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="cf86e-109">[içinde] `IID` İstenen örnek türü.</span><span class="sxs-lookup"><span data-stu-id="cf86e-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="cf86e-110">[çıkış] Arayan tarafından istenen yönetilen tür örneğine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf86e-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf86e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf86e-111">Remarks</span></span>  
 <span data-ttu-id="cf86e-112">Ortak dil çalışma süresi zaten bir işleme yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="cf86e-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="cf86e-113">Örneğin, `ClrCreateManagedInstance` işlev çağrılmadan önce [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine bir çağrı kullanılarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cf86e-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="cf86e-114">Çalışma süresi yüklenmezse, `ClrCreateManagedInstance` ilk olarak çalışma süresinin v1.0.3705'ini yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="cf86e-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="cf86e-115">Bu başarısız olursa, çalışma zamanının en son sürümünü yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="cf86e-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf86e-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf86e-116">Requirements</span></span>  
 <span data-ttu-id="cf86e-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf86e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf86e-118">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf86e-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf86e-119">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cf86e-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf86e-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf86e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf86e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf86e-121">See also</span></span>

- [<span data-ttu-id="cf86e-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cf86e-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="cf86e-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="cf86e-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

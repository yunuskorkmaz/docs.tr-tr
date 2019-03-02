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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5103490da7f3056cf95f7986b46837e059f8212f
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211838"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="b0252-102">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="b0252-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="b0252-103">Belirli bir yönetilen türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b0252-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="b0252-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0252-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="b0252-105">COM Etkinleştirme yönetilen türün bir örneğini oluşturmak için kullanabilir veya barındırma (bkz [CLR barındırma arabirimleri eklenmiş .NET Framework 4 ve 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="b0252-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0252-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0252-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0252-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0252-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="b0252-108">[in] İstenen örnek türünün adını bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b0252-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="b0252-109">[in] `IID` İstenen örnek türü.</span><span class="sxs-lookup"><span data-stu-id="b0252-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="b0252-110">[out] Çağıran tarafından istenen yönetilen türü örneğine bir işaretçi işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b0252-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0252-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0252-111">Remarks</span></span>  
 <span data-ttu-id="b0252-112">Ortak dil çalışma zamanı zaten işlem içine yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="b0252-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="b0252-113">Örneğin, bir çağrı kullanılarak yüklenebilir [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) önce işlev `ClrCreateManagedInstance` işlevi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b0252-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="b0252-114">Çalışma zamanı yüklü değilse `ClrCreateManagedInstance` ilk v1.0.3705 çalışma zamanı yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="b0252-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="b0252-115">Bu başarısız olursa, çalışma zamanının en son sürümünü yüklemeyi dener.</span><span class="sxs-lookup"><span data-stu-id="b0252-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0252-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0252-116">Requirements</span></span>  
 <span data-ttu-id="b0252-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0252-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0252-118">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b0252-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0252-119">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0252-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0252-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0252-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0252-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0252-121">See also</span></span>
- [<span data-ttu-id="b0252-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b0252-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="b0252-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="b0252-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

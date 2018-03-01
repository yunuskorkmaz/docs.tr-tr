---
title: "ClrCreateManagedInstance İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64a1bc6bbd89e3a36ac53b322bb246a7e61baa67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="bade0-102">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="bade0-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="bade0-103">Belirtilen yönetilen türü örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bade0-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="bade0-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bade0-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="bade0-105">COM Etkinleştirme yönetilen türü örneği oluşturun veya barındırma kullanın (bkz [CLR barındırma arabirimleri eklenen .NET Framework 4 ve 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="bade0-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bade0-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bade0-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bade0-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bade0-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="bade0-108">[in] İstenen örneği türünün adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bade0-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="bade0-109">[in] `IID` İstenen örneği türü.</span><span class="sxs-lookup"><span data-stu-id="bade0-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="bade0-110">[out] Çağıran tarafından istendi yönetilen türünün bir örneği için bir işaretçi bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bade0-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bade0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bade0-111">Remarks</span></span>  
 <span data-ttu-id="bade0-112">Ortak dil çalışma zamanı süreç içine önceden yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="bade0-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="bade0-113">Örneğin, bunu bir çağrı kullanılarak yüklenebilir [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) önce işlev `ClrCreateManagedInstance` işlevi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bade0-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="bade0-114">Çalışma zamanı yüklenmezse `ClrCreateManagedInstance` önce çalışma zamanının v1.0.3705 yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="bade0-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="bade0-115">Başarısız olursa, çalışma zamanı en son sürümünü yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="bade0-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bade0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bade0-116">Requirements</span></span>  
 <span data-ttu-id="bade0-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bade0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bade0-118">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bade0-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bade0-119">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bade0-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bade0-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bade0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bade0-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bade0-121">See Also</span></span>  
 [<span data-ttu-id="bade0-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bade0-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="bade0-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="bade0-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

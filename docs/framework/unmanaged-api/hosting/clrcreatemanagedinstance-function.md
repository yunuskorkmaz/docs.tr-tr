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
ms.openlocfilehash: 4e672030ae83b57da6f9ab66630513d79f28b8f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131995"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="1880b-102">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="1880b-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="1880b-103">Belirtilen yönetilen türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1880b-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="1880b-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="1880b-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="1880b-105">Yönetilen türün bir örneğini oluşturmak için COM etkinleştirmesini kullanın veya barındırma kullanın (bkz. [.NET Framework 4 ve 4,5 ' de eklenen clr barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="1880b-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1880b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1880b-106">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1880b-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1880b-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="1880b-108">'ndaki İstenen örnek türünün adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1880b-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="1880b-109">'ndaki İstenen örnek türünün `IID`.</span><span class="sxs-lookup"><span data-stu-id="1880b-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="1880b-110">dışı Çağıran tarafından istenen yönetilen tür örneğine yönelik işaretçiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1880b-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1880b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1880b-111">Remarks</span></span>  
 <span data-ttu-id="1880b-112">Ortak dil çalışma zamanının zaten bir işleme yüklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1880b-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="1880b-113">Örneğin, `ClrCreateManagedInstance` işlevi çağrılmadan önce [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) işlevine yapılan bir çağrı kullanılarak yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="1880b-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="1880b-114">Çalışma zamanı yüklü değilse, önce `ClrCreateManagedInstance` çalışma zamanının v 1.0.3705 sürümünü yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="1880b-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="1880b-115">Başarısız olursa, çalışma zamanının en son sürümünü yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="1880b-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1880b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1880b-116">Requirements</span></span>  
 <span data-ttu-id="1880b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1880b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1880b-118">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1880b-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1880b-119">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1880b-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1880b-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1880b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1880b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1880b-121">See also</span></span>

- [<span data-ttu-id="1880b-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1880b-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="1880b-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="1880b-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

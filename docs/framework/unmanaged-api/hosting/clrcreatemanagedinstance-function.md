---
description: 'Daha fazla bilgi edinin: ClrCreateManagedInstance Işlevi'
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
ms.openlocfilehash: b6d3b014f54dd563e53cd8a4c48907d01945015f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799937"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="c247e-103">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="c247e-103">ClrCreateManagedInstance Function</span></span>

<span data-ttu-id="c247e-104">Belirtilen yönetilen türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c247e-104">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="c247e-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="c247e-105">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="c247e-106">Yönetilen türün bir örneğini oluşturmak için COM etkinleştirmesini kullanın veya barındırma kullanın (bkz. [.NET Framework 4 ve 4,5 ' de eklenen clr barındırma arabirimleri](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="c247e-106">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c247e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c247e-107">Syntax</span></span>  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c247e-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c247e-108">Parameters</span></span>  

 `pTypeName`  
 <span data-ttu-id="c247e-109">'ndaki İstenen örnek türünün adına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c247e-109">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="c247e-110">'ndaki `IID` İstenen örnek türü.</span><span class="sxs-lookup"><span data-stu-id="c247e-110">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="c247e-111">dışı Çağıran tarafından istenen yönetilen tür örneğine yönelik işaretçiye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c247e-111">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c247e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c247e-112">Remarks</span></span>  

 <span data-ttu-id="c247e-113">Ortak dil çalışma zamanının zaten bir işleme yüklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c247e-113">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="c247e-114">Örneğin, işlev çağrılmadan önce [CorBindToRuntimeEx](corbindtoruntimeex-function.md) işlevine yapılan bir çağrı kullanılarak yüklenebilir `ClrCreateManagedInstance` .</span><span class="sxs-lookup"><span data-stu-id="c247e-114">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="c247e-115">Çalışma zamanı yüklü değilse, `ClrCreateManagedInstance` önce çalışma zamanının v 1.0.3705 sürümünü yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c247e-115">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="c247e-116">Başarısız olursa, çalışma zamanının en son sürümünü yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="c247e-116">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c247e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c247e-117">Requirements</span></span>  

 <span data-ttu-id="c247e-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c247e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c247e-119">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c247e-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c247e-120">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c247e-120">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c247e-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c247e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c247e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c247e-122">See also</span></span>

- [<span data-ttu-id="c247e-123">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c247e-123">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
- [<span data-ttu-id="c247e-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="c247e-124">Hosting</span></span>](index.md)

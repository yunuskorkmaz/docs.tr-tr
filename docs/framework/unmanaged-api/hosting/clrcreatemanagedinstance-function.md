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
ms.openlocfilehash: a375ea586bacc2d3dafe53d493a7467730fae889
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432327"
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="28cde-102">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="28cde-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="28cde-103">Belirtilen yönetilen türü örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28cde-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="28cde-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="28cde-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="28cde-105">COM Etkinleştirme yönetilen türü örneği oluşturun veya barındırma kullanın (bkz [CLR barındırma arabirimleri eklenen .NET Framework 4 ve 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="28cde-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28cde-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28cde-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28cde-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28cde-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="28cde-108">[in] İstenen örneği türünün adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="28cde-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="28cde-109">[in] `IID` İstenen örneği türü.</span><span class="sxs-lookup"><span data-stu-id="28cde-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="28cde-110">[out] Çağıran tarafından istendi yönetilen türünün bir örneği için bir işaretçi bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="28cde-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28cde-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28cde-111">Remarks</span></span>  
 <span data-ttu-id="28cde-112">Ortak dil çalışma zamanı süreç içine önceden yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="28cde-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="28cde-113">Örneğin, bunu bir çağrı kullanılarak yüklenebilir [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) önce işlev `ClrCreateManagedInstance` işlevi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="28cde-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="28cde-114">Çalışma zamanı yüklenmezse `ClrCreateManagedInstance` önce çalışma zamanının v1.0.3705 yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="28cde-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="28cde-115">Başarısız olursa, çalışma zamanı en son sürümünü yüklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="28cde-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28cde-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28cde-116">Requirements</span></span>  
 <span data-ttu-id="28cde-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28cde-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28cde-118">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="28cde-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="28cde-119">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28cde-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="28cde-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28cde-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28cde-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28cde-121">See Also</span></span>  
 [<span data-ttu-id="28cde-122">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="28cde-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="28cde-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="28cde-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

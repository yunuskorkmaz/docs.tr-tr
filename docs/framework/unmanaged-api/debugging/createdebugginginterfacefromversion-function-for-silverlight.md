---
title: "Silverlight için CreateDebuggingInterfaceFromVersion İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1c37609d6fe95e95b19e6ab86bbb9ce4e9e1b87a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="ed877-102">Silverlight için CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="ed877-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="ed877-103">Sunucudan döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesi kabul [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)ve karşılık gelen bir hata ayıklayıcı arabirimi döndürür (genellikle [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="ed877-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed877-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ed877-104">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed877-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ed877-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="ed877-106">[in] Tarafından döndürülen hedef ayıklayıcı CLR sürüm dizesi [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="ed877-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="ed877-107">[out] Bir COM nesnesi için bir işaretçi işaretçisine (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="ed877-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="ed877-108">Bu nesne için cast bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , döndürülmeden önce nesne.</span><span class="sxs-lookup"><span data-stu-id="ed877-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed877-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ed877-109">Return Value</span></span>  
 <span data-ttu-id="ed877-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ed877-110">S_OK</span></span>  
 <span data-ttu-id="ed877-111">`ppCordb`arabirimini uygulayan geçerli bir nesneye başvuruyor [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ed877-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="ed877-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ed877-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="ed877-113">Ya da `szDebuggeeVersion` veya `ppCordb` null.</span><span class="sxs-lookup"><span data-stu-id="ed877-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="ed877-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="ed877-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="ed877-115">CLR hata ayıklama için gerekli bir bileşeni bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="ed877-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="ed877-116">Bu, mscordbi.dll veya mscordaccore.dll CoreCLR.dll hedefi olarak aynı dizinde bulunamadığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ed877-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="ed877-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="ed877-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="ed877-118">Mscordbi.dll veya mscordaccore.dll CoreCLR.dll hedef aynı sürümde değil.</span><span class="sxs-lookup"><span data-stu-id="ed877-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="ed877-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="ed877-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ed877-120">İade edilemiyor bir [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ed877-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed877-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed877-121">Remarks</span></span>  
 <span data-ttu-id="ed877-122">Döndürülen arabirimi bir hedef işlemde bir CLR ekleme ve CLR çalıştıran yönetilen kodda hata ayıklama için olanakları sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed877-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed877-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed877-123">Requirements</span></span>  
 <span data-ttu-id="ed877-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed877-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed877-125">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="ed877-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="ed877-126">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="ed877-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="ed877-127">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ed877-127">**.NET Framework Versions:** 3.5 SP1</span></span>

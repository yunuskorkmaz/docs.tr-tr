---
title: Silverlight için CreateDebuggingInterfaceFromVersion İşlevi
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96968956b513e1ae80a25f5fb4afea48bf888876
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739269"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="f0515-102">Silverlight için CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="f0515-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="f0515-103">Öğesinden döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesini kabul eder [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)ve karşılık gelen bir hata ayıklayıcı arabirim döndürür (genelde [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="f0515-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0515-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0515-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0515-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0515-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="f0515-106">[in] Hedef hata ayıklanan tarafından döndürülen CLR sürüm dizesi [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="f0515-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="f0515-107">[out] Bir COM nesnesine bir işaretçi işaretçisi (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="f0515-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="f0515-108">Bu nesne için atayın bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) döndürülmeden önce nesne.</span><span class="sxs-lookup"><span data-stu-id="f0515-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0515-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f0515-109">Return Value</span></span>  
 <span data-ttu-id="f0515-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0515-110">S_OK</span></span>  
 <span data-ttu-id="f0515-111">`ppCordb` uygulayan geçerli bir nesneye başvuruda [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f0515-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="f0515-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f0515-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="f0515-113">Ya da `szDebuggeeVersion` veya `ppCordb` null.</span><span class="sxs-lookup"><span data-stu-id="f0515-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="f0515-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="f0515-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="f0515-115">CLR hata ayıklama için gerekli olan bir bileşeni bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="f0515-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="f0515-116">Bu, mscordbi.dll ya da mscordaccore.dll CoreCLR.dll hedef ile aynı dizinde bulunamadığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f0515-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="f0515-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="f0515-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="f0515-118">Mscordbi.dll ya da mscordaccore.dll CoreCLR.dll hedefi olarak aynı sürüm değil.</span><span class="sxs-lookup"><span data-stu-id="f0515-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="f0515-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="f0515-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f0515-120">Döndürülemiyor bir [Icordebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f0515-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0515-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0515-121">Remarks</span></span>  
 <span data-ttu-id="f0515-122">Döndürülen arabirim için bir hedef işlemde bir CLR ekleme ve CLR çalışan yönetilen kodda hata ayıklama özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0515-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0515-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0515-123">Requirements</span></span>  
 <span data-ttu-id="f0515-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0515-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0515-125">**Başlık:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="f0515-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="f0515-126">**Kitaplığı:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="f0515-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="f0515-127">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f0515-127">**.NET Framework Versions:** 3.5 SP1</span></span>

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
ms.openlocfilehash: 85b5a5a630f399d0e036de434365e2e4f8f02dea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793837"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="e72da-102">Silverlight için CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="e72da-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="e72da-103">[CreateVersionStringFromModule işlevinden](createversionstringfrommodule-function.md)döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimini (genellikle, [ICorDebug](icordebug-interface.md)) döndürür.</span><span class="sxs-lookup"><span data-stu-id="e72da-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e72da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e72da-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e72da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e72da-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="e72da-106">'ndaki [CreateVersionStringFromModule işlevi](createversionstringfrommodule-function.md)tarafından döndürülen hedef hata ayıklanan clr 'nin sürüm dizesi.</span><span class="sxs-lookup"><span data-stu-id="e72da-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="e72da-107">dışı COM nesnesi işaretçisi işaretçisi (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="e72da-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="e72da-108">Bu nesne, döndürülmeden önce bir [ICorDebug](icordebug-interface.md) nesnesine atacaktır.</span><span class="sxs-lookup"><span data-stu-id="e72da-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e72da-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e72da-109">Return Value</span></span>  
 <span data-ttu-id="e72da-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e72da-110">S_OK</span></span>  
 <span data-ttu-id="e72da-111">`ppCordb` [ICorDebug arabirimi](icordebug-interface.md) arabirimini uygulayan geçerli bir nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="e72da-111">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="e72da-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e72da-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="e72da-113">`szDebuggeeVersion` ya da `ppCordb` null.</span><span class="sxs-lookup"><span data-stu-id="e72da-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="e72da-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="e72da-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="e72da-115">CLR hata ayıklaması için gerekli bir bileşen bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="e72da-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="e72da-116">Bu, mscordbi. dll veya mscordaccore. dll ' nin hedef CoreCLR. dll ile aynı dizinde bulunamadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e72da-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="e72da-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="e72da-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="e72da-118">Mscordbi. dll veya mscordaccore. dll, hedef CoreCLR. dll ile aynı sürümde değil.</span><span class="sxs-lookup"><span data-stu-id="e72da-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="e72da-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="e72da-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e72da-120">[ICorDebug arabirimi](icordebug-interface.md)döndürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="e72da-120">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e72da-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e72da-121">Remarks</span></span>  
 <span data-ttu-id="e72da-122">Döndürülen arabirim, hedef işlemdeki bir CLR 'ye ekleme ve CLR 'nin çalıştığı yönetilen kodda hata ayıklama için tesisler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e72da-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e72da-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e72da-123">Requirements</span></span>  
 <span data-ttu-id="e72da-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e72da-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e72da-125">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="e72da-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="e72da-126">**Kitaplık:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="e72da-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="e72da-127">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e72da-127">**.NET Framework Versions:** 3.5 SP1</span></span>

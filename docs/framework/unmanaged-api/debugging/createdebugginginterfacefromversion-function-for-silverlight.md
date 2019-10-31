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
ms.openlocfilehash: 438af9f191f48a86207c3b343ba428eef2c1fabc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132196"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="a5c35-102">Silverlight için CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="a5c35-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="a5c35-103">[CreateVersionStringFromModule işlevinden](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimini (genellikle, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)) döndürür.</span><span class="sxs-lookup"><span data-stu-id="a5c35-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c35-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5c35-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5c35-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5c35-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="a5c35-106">'ndaki [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)tarafından döndürülen hedef hata ayıklanan clr 'nin sürüm dizesi.</span><span class="sxs-lookup"><span data-stu-id="a5c35-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="a5c35-107">dışı COM nesnesi işaretçisi işaretçisi (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="a5c35-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="a5c35-108">Bu nesne, döndürülmeden önce bir [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesnesine atacaktır.</span><span class="sxs-lookup"><span data-stu-id="a5c35-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5c35-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a5c35-109">Return Value</span></span>  
 <span data-ttu-id="a5c35-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5c35-110">S_OK</span></span>  
 <span data-ttu-id="a5c35-111">`ppCordb` [ICorDebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimini uygulayan geçerli bir nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="a5c35-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="a5c35-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a5c35-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="a5c35-113">`szDebuggeeVersion` ya da `ppCordb` null.</span><span class="sxs-lookup"><span data-stu-id="a5c35-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="a5c35-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="a5c35-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="a5c35-115">CLR hata ayıklaması için gerekli bir bileşen bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="a5c35-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="a5c35-116">Bu, mscordbi. dll veya mscordaccore. dll ' nin hedef CoreCLR. dll ile aynı dizinde bulunamadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a5c35-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a5c35-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="a5c35-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="a5c35-118">Mscordbi. dll veya mscordaccore. dll, hedef CoreCLR. dll ile aynı sürümde değil.</span><span class="sxs-lookup"><span data-stu-id="a5c35-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="a5c35-119">E_FAıL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="a5c35-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a5c35-120">[ICorDebug arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)döndürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="a5c35-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c35-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5c35-121">Remarks</span></span>  
 <span data-ttu-id="a5c35-122">Döndürülen arabirim, hedef işlemdeki bir CLR 'ye ekleme ve CLR 'nin çalıştığı yönetilen kodda hata ayıklama için tesisler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5c35-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c35-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5c35-123">Requirements</span></span>  
 <span data-ttu-id="a5c35-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5c35-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c35-125">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="a5c35-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a5c35-126">**Kitaplık:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="a5c35-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a5c35-127">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a5c35-127">**.NET Framework Versions:** 3.5 SP1</span></span>

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
ms.openlocfilehash: c83bdcca4fab75b4ae94500ceb785b6000cd802a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860872"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="02448-102">Silverlight için CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="02448-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="02448-103">[CreateVersionStringFromModule işlevinden](createversionstringfrommodule-function.md)döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimini (genellikle, [ICorDebug](icordebug-interface.md)) döndürür.</span><span class="sxs-lookup"><span data-stu-id="02448-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02448-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02448-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02448-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02448-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="02448-106">'ndaki [CreateVersionStringFromModule işlevi](createversionstringfrommodule-function.md)tarafından döndürülen hedef hata ayıklanan clr 'nin sürüm dizesi.</span><span class="sxs-lookup"><span data-stu-id="02448-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="02448-107">dışı COM nesnesine (`IUnknown`) yönelik işaretçiye yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="02448-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="02448-108">Bu nesne, döndürülmeden önce bir [ICorDebug](icordebug-interface.md) nesnesine atacaktır.</span><span class="sxs-lookup"><span data-stu-id="02448-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02448-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="02448-109">Return Value</span></span>  
 <span data-ttu-id="02448-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="02448-110">S_OK</span></span>  
 <span data-ttu-id="02448-111">`ppCordb`[ICorDebug arabirimi](icordebug-interface.md) arabirimini uygulayan geçerli bir nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="02448-111">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="02448-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="02448-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="02448-113">Ya `szDebuggeeVersion` `ppCordb` da null.</span><span class="sxs-lookup"><span data-stu-id="02448-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="02448-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="02448-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="02448-115">CLR hata ayıklaması için gerekli bir bileşen bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="02448-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="02448-116">Bu, mscordbi. dll veya mscordaccore. dll ' nin hedef CoreCLR. dll ile aynı dizinde bulunamadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="02448-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="02448-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="02448-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="02448-118">Mscordbi. dll veya mscordaccore. dll, hedef CoreCLR. dll ile aynı sürümde değil.</span><span class="sxs-lookup"><span data-stu-id="02448-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="02448-119">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="02448-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="02448-120">[ICorDebug arabirimi](icordebug-interface.md)döndürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="02448-120">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02448-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02448-121">Remarks</span></span>  
 <span data-ttu-id="02448-122">Döndürülen arabirim, hedef işlemdeki bir CLR 'ye ekleme ve CLR 'nin çalıştığı yönetilen kodda hata ayıklama için tesisler sağlar.</span><span class="sxs-lookup"><span data-stu-id="02448-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02448-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02448-123">Requirements</span></span>  
 <span data-ttu-id="02448-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02448-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02448-125">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="02448-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="02448-126">**Kitaplık:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="02448-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="02448-127">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="02448-127">**.NET Framework Versions:** 3.5 SP1</span></span>

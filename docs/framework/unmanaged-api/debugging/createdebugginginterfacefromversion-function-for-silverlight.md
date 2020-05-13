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
ms.openlocfilehash: f40345b09cae164660711b987f62130518736518
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208630"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="c0855-102">Silverlight için CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="c0855-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>

<span data-ttu-id="c0855-103">[CreateVersionStringFromModule işlevinden](createversionstringfrommodule-function.md)döndürülen ortak dil çalışma zamanı (CLR) sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimini (genellikle, [ICorDebug](icordebug-interface.md)) döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0855-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0855-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0855-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0855-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0855-105">Parameters</span></span>  

 `szDebuggeeVersion`\
 <span data-ttu-id="c0855-106">'ndaki [CreateVersionStringFromModule işlevi](createversionstringfrommodule-function.md)tarafından döndürülen hedef hata ayıklanan clr 'nin sürüm dizesi.</span><span class="sxs-lookup"><span data-stu-id="c0855-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`\
 <span data-ttu-id="c0855-107">dışı COM nesnesine () yönelik işaretçiye yönelik işaretçi `IUnknown` .</span><span class="sxs-lookup"><span data-stu-id="c0855-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="c0855-108">Bu nesne, döndürülmeden önce bir [ICorDebug](icordebug-interface.md) nesnesine atacaktır.</span><span class="sxs-lookup"><span data-stu-id="c0855-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0855-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0855-109">Return Value</span></span>

 `S_OK`\
 <span data-ttu-id="c0855-110">`ppCordb`[ICorDebug arabirimi](icordebug-interface.md) arabirimini uygulayan geçerli bir nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="c0855-110">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 `E_INVALIDARG`\
 <span data-ttu-id="c0855-111">`szDebuggeeVersion`Ya da `ppCordb` null.</span><span class="sxs-lookup"><span data-stu-id="c0855-111">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 <span data-ttu-id="c0855-112">CLR hata ayıklaması için gerekli bir bileşen bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="c0855-112">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="c0855-113">_Mscordbi. dll_ veya _mscordaccore. dll_ , hedef CoreCLR. dll ile aynı dizinde bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="c0855-113">Either _mscordbi.dll_ or _mscordaccore.dll_ was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 <span data-ttu-id="c0855-114">Mscordbi. dll veya mscordaccore. dll, hedef CoreCLR. dll ile aynı sürümde değil.</span><span class="sxs-lookup"><span data-stu-id="c0855-114">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="c0855-115">`E_FAIL`(veya diğer `E_` dönüş kodları) </span><span class="sxs-lookup"><span data-stu-id="c0855-115">`E_FAIL` (or other `E_` return codes)</span></span>\
 <span data-ttu-id="c0855-116">[ICorDebug arabirimi](icordebug-interface.md)döndürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="c0855-116">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0855-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0855-117">Remarks</span></span>

 <span data-ttu-id="c0855-118">Döndürülen arabirim, hedef işlemdeki bir CLR 'ye ekleme ve CLR 'nin çalıştığı yönetilen kodda hata ayıklama için tesisler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0855-118">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0855-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0855-119">Requirements</span></span>

 <span data-ttu-id="c0855-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0855-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0855-121">**Üstbilgi:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="c0855-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="c0855-122">**Kitaplık:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="c0855-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="c0855-123">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c0855-123">**.NET Framework Versions:** 3.5 SP1</span></span>

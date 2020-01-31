---
title: ICorDebugFunction2::GetVersionNumber Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type:
- apiref
ms.openlocfilehash: d85885d750f3c98e46b3e44418564da18850d3ec
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794495"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="765fe-102">ICorDebugFunction2::GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="765fe-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="765fe-103">Bu işlevin Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="765fe-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="765fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="765fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="765fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="765fe-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="765fe-106">dışı Bu ICorDebugFunction2 nesnesi tarafından temsil edilen işlevin sürüm numarası olan tamsayıya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="765fe-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="765fe-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="765fe-107">Remarks</span></span>  
 <span data-ttu-id="765fe-108">Çalışma zamanı, hata ayıklama oturumu sırasında her bir modüle gerçekleşen düzenleme sayısını izler.</span><span class="sxs-lookup"><span data-stu-id="765fe-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="765fe-109">Bir işlevin sürüm numarası, işlevi sunan düzenleme sayısından bir daha fazla.</span><span class="sxs-lookup"><span data-stu-id="765fe-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="765fe-110">İşlevin özgün sürümü sürüm 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="765fe-110">The function's original version is version 1.</span></span> <span data-ttu-id="765fe-111">Bu modülde her [ICorDebugModule2:: ApplyChanges](icordebugmodule2-applychanges-method.md) çağrıldığında sayı bir modül için artırılır.</span><span class="sxs-lookup"><span data-stu-id="765fe-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="765fe-112">Bu nedenle, bir işlevin gövdesi `ICorDebugModule2::ApplyChanges`ilk ve üçüncü çağrısında değiştirildiyse, `GetVersionNumber` söz konusu işlev için sürüm 1, 2 veya 4 döndürebilir, sürüm 3 ' ü içermez.</span><span class="sxs-lookup"><span data-stu-id="765fe-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="765fe-113">(Bu işlevin sürüm 3 ' ü yoktur.)</span><span class="sxs-lookup"><span data-stu-id="765fe-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="765fe-114">Sürüm numarası her modül için ayrı olarak izlenir.</span><span class="sxs-lookup"><span data-stu-id="765fe-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="765fe-115">Bu nedenle, modül 1 üzerinde dört düzenleme gerçekleştirirseniz ve modül 2 ' de hiç bir işlem yaptıysanız, modül 1 ' deki bir sonraki düzenleme, modül 1 ' deki tüm düzenlenmiş işlevlere 6 sürüm numarası atar.</span><span class="sxs-lookup"><span data-stu-id="765fe-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="765fe-116">Aynı düzenleme, modül 2 ' ye dokunursa modül 2 ' deki işlevler sürüm numarası 2 alır.</span><span class="sxs-lookup"><span data-stu-id="765fe-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="765fe-117">`GetVersionNumber` yöntemi tarafından edinilen sürüm numarası [ICorDebugFunction:: GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md)tarafından elde edilenden daha düşük olabilir.</span><span class="sxs-lookup"><span data-stu-id="765fe-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="765fe-118">[ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) yöntemi, `ICorDebugFunction2::GetVersionNumber`ile aynı işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="765fe-118">The [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="765fe-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="765fe-119">Requirements</span></span>  
 <span data-ttu-id="765fe-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="765fe-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="765fe-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="765fe-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="765fe-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="765fe-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="765fe-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="765fe-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

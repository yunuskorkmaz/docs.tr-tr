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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89cf2a12b0a693bbed3e8a3c1134d0f2b2a72a30
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754456"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="9fc9a-102">ICorDebugFunction2::GetVersionNumber Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9fc9a-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="9fc9a-103">Bu işlev Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fc9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fc9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fc9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9fc9a-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="9fc9a-106">[out] Sürüm numarasını bu Icordebugfunction2 nesnesi tarafından temsil edilen işlev bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fc9a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fc9a-107">Remarks</span></span>  
 <span data-ttu-id="9fc9a-108">Çalışma zamanı, her modül için hata ayıklama oturumu sırasında meydana gelen düzenlemeleri sayısını izler.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="9fc9a-109">Bir işlev sürüm numarasını biridir işlevi sunulan düzenleme sayısından daha fazla.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="9fc9a-110">İşlevin özgün sürüm 1 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-110">The function's original version is version 1.</span></span> <span data-ttu-id="9fc9a-111">Sayı, her bir modül için artırılır [Icordebugmodule2::applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) üzerinde bu modül çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="9fc9a-112">Bu nedenle, ilk ve üçüncü aramasında bir işlev gövdesini değiştirildiyse `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` sürüm 1, 2 veya 4: Bu işlev, ancak sürüm 3 döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="9fc9a-113">(İşlev sürüm 3 olması.)</span><span class="sxs-lookup"><span data-stu-id="9fc9a-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="9fc9a-114">Sürüm numarası, her modül için ayrı ayrı izlenir.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="9fc9a-115">Modül 1 ve 2 modül yok dört düzenlemeler yapabilirsiniz, bu nedenle, sonraki düzenlemeniz modülü 1 sürüm numarası 6 modülü 1 düzenlenen tüm işlevler için atar.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="9fc9a-116">Aynı dokunmalar Modül 2 düzenlerseniz, Modül 2 işlevleri sürüm numarası 2 olarak alırsınız.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="9fc9a-117">Sürüm numarası elde tarafından `GetVersionNumber` yöntemi tarafından alınan daha düşük [ICorDebugFunction::getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="9fc9a-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="9fc9a-118">[Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) yöntemi olarak aynı işlemi yapar `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="9fc9a-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fc9a-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fc9a-119">Requirements</span></span>  
 <span data-ttu-id="9fc9a-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fc9a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fc9a-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fc9a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fc9a-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fc9a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fc9a-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fc9a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

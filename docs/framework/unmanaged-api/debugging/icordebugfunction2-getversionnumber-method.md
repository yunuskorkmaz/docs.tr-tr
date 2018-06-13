---
title: ICorDebugFunction2::GetVersionNumber Metodu
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
ms.openlocfilehash: fdd2151c4886959647de4f9e27a20a93ffc07429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420059"
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="4f34b-102">ICorDebugFunction2::GetVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="4f34b-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="4f34b-103">Bu işlev Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="4f34b-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f34b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f34b-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f34b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f34b-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="4f34b-106">[out] Bu Icordebugfunction2 nesnesi tarafından temsil edilen işlevi sürüm sayısı bir tamsayı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4f34b-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f34b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f34b-107">Remarks</span></span>  
 <span data-ttu-id="4f34b-108">Çalışma zamanı, her modül için bir hata ayıklama oturumu sırasında yapılmadığı düzenlemeleri sayısını izler.</span><span class="sxs-lookup"><span data-stu-id="4f34b-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="4f34b-109">Bir işlevin sürüm numarası biridir işlevi sunulan düzenleme sayıdan fazla.</span><span class="sxs-lookup"><span data-stu-id="4f34b-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="4f34b-110">İşlevin özgün sürüm 1 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="4f34b-110">The function's original version is version 1.</span></span> <span data-ttu-id="4f34b-111">Sayı, her seferinde bir modülü için artırılır [Icordebugmodule2::applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) üzerinde bu modül çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4f34b-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="4f34b-112">Bu nedenle, bir işlevin gövdesi birinci ve üçüncü çağrısında değiştirilmişse `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` sürüm 1, 2 veya 4 Bu işlevin, ancak sürüm 3 döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="4f34b-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="4f34b-113">(İşlev hiçbir sürüm 3 olması.)</span><span class="sxs-lookup"><span data-stu-id="4f34b-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="4f34b-114">Sürüm numarası, her modül için ayrı olarak izlenir.</span><span class="sxs-lookup"><span data-stu-id="4f34b-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="4f34b-115">Modül 1 ve hiçbiri modülü 2 dört düzenlemeleri gerçekleştirirseniz, bu nedenle, sonraki düzenlemeniz modülü 1 sürüm numarası 6 olarak düzenlenen uygulamasında tüm işlevleri Modül 1 atar.</span><span class="sxs-lookup"><span data-stu-id="4f34b-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="4f34b-116">Aynı rötuşları Modül 2 düzenlerseniz, Modül 2 işlevlerde 2 sürüm sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4f34b-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="4f34b-117">Sürüm numarasını elde tarafından `GetVersionNumber` yöntemi tarafından edindiğiniz daha düşük [ICorDebugFunction::getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="4f34b-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="4f34b-118">[Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) yöntemi olarak aynı işlemi gerçekleştirir `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="4f34b-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f34b-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f34b-119">Requirements</span></span>  
 <span data-ttu-id="4f34b-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f34b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f34b-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f34b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f34b-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f34b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f34b-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f34b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugFunction2::GetVersionNumber Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.GetVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::GetVersionNumber
helpviewer_keywords:
- ICorDebugFunction2::GetVersionNumber method [.NET Framework debugging]
- GetVersionNumber method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: e3a1ce48-9bb9-4ed6-a5fe-5e1819a6333f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16902d1a50f691ae555fdbc964bb9a1c6bf563c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2getversionnumber-method"></a><span data-ttu-id="cddc0-102">ICorDebugFunction2::GetVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="cddc0-102">ICorDebugFunction2::GetVersionNumber Method</span></span>
<span data-ttu-id="cddc0-103">Bu işlev Düzenle ve devam et sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="cddc0-103">Gets the Edit and Continue version of this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cddc0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cddc0-104">Syntax</span></span>  
  
```  
HRESULT GetVersionNumber (  
    [out] ULONG32   *pnVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cddc0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cddc0-105">Parameters</span></span>  
 `pnVersion`  
 <span data-ttu-id="cddc0-106">[out] Bu Icordebugfunction2 nesnesi tarafından temsil edilen işlevi sürüm sayısı bir tamsayı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cddc0-106">[out] A pointer to an integer that is the version number of the function that is represented by this ICorDebugFunction2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cddc0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cddc0-107">Remarks</span></span>  
 <span data-ttu-id="cddc0-108">Çalışma zamanı, her modül için bir hata ayıklama oturumu sırasında yapılmadığı düzenlemeleri sayısını izler.</span><span class="sxs-lookup"><span data-stu-id="cddc0-108">The runtime keeps track of the number of edits that have taken place to each module during a debug session.</span></span> <span data-ttu-id="cddc0-109">Bir işlevin sürüm numarası biridir işlevi sunulan düzenleme sayıdan fazla.</span><span class="sxs-lookup"><span data-stu-id="cddc0-109">The version number of a function is one more than the number of the edit that introduced the function.</span></span> <span data-ttu-id="cddc0-110">İşlevin özgün sürüm 1 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="cddc0-110">The function's original version is version 1.</span></span> <span data-ttu-id="cddc0-111">Sayı, her seferinde bir modülü için artırılır [Icordebugmodule2::applychanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) üzerinde bu modül çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cddc0-111">The number is incremented for a module every time [ICorDebugModule2::ApplyChanges](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md) is called on that module.</span></span> <span data-ttu-id="cddc0-112">Bu nedenle, bir işlevin gövdesi birinci ve üçüncü çağrısında değiştirilmişse `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` sürüm 1, 2 veya 4 Bu işlevin, ancak sürüm 3 döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="cddc0-112">Thus, if a function’s body was replaced in the first and third call to `ICorDebugModule2::ApplyChanges`, `GetVersionNumber` may return version 1, 2, or 4 for that function, but not version 3.</span></span> <span data-ttu-id="cddc0-113">(İşlev hiçbir sürüm 3 olması.)</span><span class="sxs-lookup"><span data-stu-id="cddc0-113">(That function would have no version 3.)</span></span>  
  
 <span data-ttu-id="cddc0-114">Sürüm numarası, her modül için ayrı olarak izlenir.</span><span class="sxs-lookup"><span data-stu-id="cddc0-114">The version number is tracked separately for each module.</span></span> <span data-ttu-id="cddc0-115">Modül 1 ve hiçbiri modülü 2 dört düzenlemeleri gerçekleştirirseniz, bu nedenle, sonraki düzenlemeniz modülü 1 sürüm numarası 6 olarak düzenlenen uygulamasında tüm işlevleri Modül 1 atar.</span><span class="sxs-lookup"><span data-stu-id="cddc0-115">So, if you perform four edits on Module 1, and none on Module 2, your next edit on Module 1 will assign a version number of 6 to all the edited functions in Module 1.</span></span> <span data-ttu-id="cddc0-116">Aynı rötuşları Modül 2 düzenlerseniz, Modül 2 işlevlerde 2 sürüm sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cddc0-116">If the same edit touches Module 2, the functions in Module 2 will get a version number of 2.</span></span>  
  
 <span data-ttu-id="cddc0-117">Sürüm numarasını elde tarafından `GetVersionNumber` yöntemi tarafından edindiğiniz daha düşük [ICorDebugFunction::getcurrentversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span><span class="sxs-lookup"><span data-stu-id="cddc0-117">The version number obtained by the `GetVersionNumber` method may be lower than that obtained by [ICorDebugFunction::GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md).</span></span>  
  
 <span data-ttu-id="cddc0-118">[Icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) yöntemi olarak aynı işlemi gerçekleştirir `ICorDebugFunction2::GetVersionNumber`.</span><span class="sxs-lookup"><span data-stu-id="cddc0-118">The [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method performs the same operation as `ICorDebugFunction2::GetVersionNumber`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cddc0-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cddc0-119">Requirements</span></span>  
 <span data-ttu-id="cddc0-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cddc0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cddc0-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cddc0-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cddc0-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cddc0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cddc0-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cddc0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
title: ICorDebugFunction::GetCurrentVersionNumber Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: 14579d4c84be9bb225e618715b3a7d45ccaac0a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728153"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="ac0e9-102">ICorDebugFunction::GetCurrentVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="ac0e9-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>

<span data-ttu-id="ac0e9-103">Bu ICorDebugFunction nesnesi tarafından temsil edilen işlevde yapılan en son düzenlemenin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac0e9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ac0e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac0e9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac0e9-105">Parameters</span></span>  

 `pnCurrentVersion`  
 <span data-ttu-id="ac0e9-106">dışı Bu işlevde yapılan en son düzenlemenin sürüm numarası olan bir tamsayı değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac0e9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac0e9-107">Remarks</span></span>  

 <span data-ttu-id="ac0e9-108">Bu işlevde yapılan en son düzenlemenin sürüm numarası, işlevin sürüm numarasından daha büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="ac0e9-109">İşlevin sürüm numarasını almak için [ICorDebugFunction2:: GetVersionNumber](icordebugfunction2-getversionnumber-method.md) yöntemini veya [ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac0e9-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac0e9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac0e9-110">Requirements</span></span>  

 <span data-ttu-id="ac0e9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac0e9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac0e9-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ac0e9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ac0e9-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ac0e9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac0e9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac0e9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

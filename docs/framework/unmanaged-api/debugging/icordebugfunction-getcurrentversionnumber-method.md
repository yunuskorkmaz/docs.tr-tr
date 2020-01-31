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
ms.openlocfilehash: 5e080e9aa89816b24aa2eb1b6b1be823922e86fb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794514"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="96a8c-102">ICorDebugFunction::GetCurrentVersionNumber Metodu</span><span class="sxs-lookup"><span data-stu-id="96a8c-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="96a8c-103">Bu ICorDebugFunction nesnesi tarafından temsil edilen işlevde yapılan en son düzenlemenin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="96a8c-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a8c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96a8c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96a8c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96a8c-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="96a8c-106">dışı Bu işlevde yapılan en son düzenlemenin sürüm numarası olan bir tamsayı değerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96a8c-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96a8c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96a8c-107">Remarks</span></span>  
 <span data-ttu-id="96a8c-108">Bu işlevde yapılan en son düzenlemenin sürüm numarası, işlevin sürüm numarasından daha büyük olabilir.</span><span class="sxs-lookup"><span data-stu-id="96a8c-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="96a8c-109">İşlevin sürüm numarasını almak için [ICorDebugFunction2:: GetVersionNumber](icordebugfunction2-getversionnumber-method.md) yöntemini veya [ICorDebugCode:: GetVersionNumber](icordebugcode-getversionnumber-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="96a8c-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96a8c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96a8c-110">Requirements</span></span>  
 <span data-ttu-id="96a8c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96a8c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96a8c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96a8c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96a8c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="96a8c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96a8c-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96a8c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

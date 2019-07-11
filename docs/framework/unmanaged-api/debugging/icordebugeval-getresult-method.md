---
title: ICorDebugEval::GetResult Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b12ba5ad5c85643d1f4c91585cf7abca210d22bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752945"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="decfc-102">ICorDebugEval::GetResult Yöntemi</span><span class="sxs-lookup"><span data-stu-id="decfc-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="decfc-103">Bu değerlendirme sonuçlarını alır.</span><span class="sxs-lookup"><span data-stu-id="decfc-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="decfc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="decfc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="decfc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="decfc-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="decfc-106">[out] Değerlendirme normalde tamamlanırsa Bu değerlendirme sonuçlarını temsil eden bir Icordebugvalue nesnenin adresini işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="decfc-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="decfc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="decfc-107">Remarks</span></span>  
 <span data-ttu-id="decfc-108">`GetResult` Yöntemi, yalnızca değerlendirme tamamlandıktan sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="decfc-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="decfc-109">Normalde, değerlendirme tamamlanırsa `ppResult` sonuçları belirtir.</span><span class="sxs-lookup"><span data-stu-id="decfc-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="decfc-110">Bir özel durumla sona ererse, oluşturulan özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="decfc-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="decfc-111">Değerlendirme için yeni bir nesne ise, yeni nesneye başvuru sonucudur.</span><span class="sxs-lookup"><span data-stu-id="decfc-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="decfc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="decfc-112">Requirements</span></span>  
 <span data-ttu-id="decfc-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="decfc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="decfc-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="decfc-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="decfc-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="decfc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="decfc-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="decfc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

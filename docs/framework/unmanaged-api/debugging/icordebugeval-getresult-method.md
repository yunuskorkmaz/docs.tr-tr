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
ms.openlocfilehash: b8e7fcb4f44d6bdf6f18c93b1046b549331621a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667125"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="c06f2-102">ICorDebugEval::GetResult Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c06f2-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="c06f2-103">Bu değerlendirme sonuçlarını alır.</span><span class="sxs-lookup"><span data-stu-id="c06f2-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c06f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c06f2-104">Syntax</span></span>  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c06f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c06f2-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="c06f2-106">[out] Değerlendirme normalde tamamlanırsa Bu değerlendirme sonuçlarını temsil eden bir Icordebugvalue nesnenin adresini işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c06f2-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c06f2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c06f2-107">Remarks</span></span>  
 <span data-ttu-id="c06f2-108">`GetResult` Yöntemi, yalnızca değerlendirme tamamlandıktan sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c06f2-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="c06f2-109">Normalde, değerlendirme tamamlanırsa `ppResult` sonuçları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c06f2-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="c06f2-110">Bir özel durumla sona ererse, oluşturulan özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="c06f2-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="c06f2-111">Değerlendirme için yeni bir nesne ise, yeni nesneye başvuru sonucudur.</span><span class="sxs-lookup"><span data-stu-id="c06f2-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c06f2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c06f2-112">Requirements</span></span>  
 <span data-ttu-id="c06f2-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c06f2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c06f2-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c06f2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c06f2-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c06f2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c06f2-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c06f2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

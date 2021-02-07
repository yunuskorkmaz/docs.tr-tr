---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgeval:: GetResult yöntemi'
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
ms.openlocfilehash: 03ab00f5c9a538e11a2046da9cbfd5ad7225231c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694246"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="b403d-103">ICorDebugEval::GetResult Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b403d-103">ICorDebugEval::GetResult Method</span></span>

<span data-ttu-id="b403d-104">Bu değerlendirmenin sonuçlarını alır.</span><span class="sxs-lookup"><span data-stu-id="b403d-104">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b403d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b403d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b403d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b403d-106">Parameters</span></span>  

 `ppResult`  
 <span data-ttu-id="b403d-107">dışı Değerlendirme normal şekilde tamamlanırsa, bu değerlendirmenin sonuçlarını temsil eden bir ICorDebugValue nesnesinin adresine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b403d-107">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b403d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b403d-108">Remarks</span></span>  

 <span data-ttu-id="b403d-109">`GetResult`Yöntem yalnızca değerlendirme tamamlandıktan sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b403d-109">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="b403d-110">Değerlendirme normal şekilde tamamlanırsa, `ppResult` sonuçları belirtir.</span><span class="sxs-lookup"><span data-stu-id="b403d-110">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="b403d-111">Bir özel durumla sonlandığında sonuç, oluşturulan özel durumdur.</span><span class="sxs-lookup"><span data-stu-id="b403d-111">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="b403d-112">Değerlendirme yeni bir nesne için ise, sonuç yeni nesneye başvurudur.</span><span class="sxs-lookup"><span data-stu-id="b403d-112">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b403d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b403d-113">Requirements</span></span>  

 <span data-ttu-id="b403d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b403d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b403d-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b403d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b403d-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b403d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b403d-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b403d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

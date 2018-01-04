---
title: ICorDebugEval::GetResult Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.GetResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f3d17e28686d1697417dd380782b1f037e0b5a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="32297-102">ICorDebugEval::GetResult Metodu</span><span class="sxs-lookup"><span data-stu-id="32297-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="32297-103">Bu değerlendirme sonuçlarını alır.</span><span class="sxs-lookup"><span data-stu-id="32297-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32297-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32297-104">Syntax</span></span>  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32297-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32297-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="32297-106">[out] İşaretçi değerlendirme normalde tamamlarsa, bu değerlendirme sonuçlarını temsil eden Icordebugvalue nesne adresine.</span><span class="sxs-lookup"><span data-stu-id="32297-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32297-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32297-107">Remarks</span></span>  
 <span data-ttu-id="32297-108">`GetResult` Yöntemi, yalnızca değerlendirme tamamlandıktan sonra geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="32297-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="32297-109">Değerlendirme normalde tamamlarsa `ppResult` sonuçları belirtir.</span><span class="sxs-lookup"><span data-stu-id="32297-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="32297-110">Bir özel durumla sona ererse, oluşturulan özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="32297-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="32297-111">Değerlendirme için yeni bir nesne varsa, yeni nesne başvurusunu sonucudur.</span><span class="sxs-lookup"><span data-stu-id="32297-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32297-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32297-112">Requirements</span></span>  
 <span data-ttu-id="32297-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32297-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32297-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32297-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32297-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32297-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32297-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32297-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

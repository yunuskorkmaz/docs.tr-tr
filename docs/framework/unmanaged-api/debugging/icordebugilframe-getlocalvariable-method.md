---
description: ': ICorDebugILFrame:: GetLocalVariable metodu hakkında daha fazla bilgi edinin'
title: ICorDebugILFrame::GetLocalVariable Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
ms.openlocfilehash: c4bb3e5a5d970539607efbaf55f3f7f08f7e72af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791380"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="be2d1-103">ICorDebugILFrame::GetLocalVariable Metodu</span><span class="sxs-lookup"><span data-stu-id="be2d1-103">ICorDebugILFrame::GetLocalVariable Method</span></span>

<span data-ttu-id="be2d1-104">Bu Microsoft ara dili (MSIL) yığın çerçevesinde belirtilen yerel değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="be2d1-104">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be2d1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be2d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be2d1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be2d1-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="be2d1-107">'ndaki Bu MSIL yığın çerçevesindeki yerel değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="be2d1-107">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="be2d1-108">dışı Alınan değeri temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="be2d1-108">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be2d1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be2d1-109">Remarks</span></span>  

 <span data-ttu-id="be2d1-110">`GetLocalVariable`Yöntemi, BIR MSIL yığın çerçevesinde veya tam zamanında (JIT) derlenmiş bir çerçevede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be2d1-110">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be2d1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be2d1-111">Requirements</span></span>  

 <span data-ttu-id="be2d1-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be2d1-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be2d1-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be2d1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be2d1-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="be2d1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be2d1-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be2d1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

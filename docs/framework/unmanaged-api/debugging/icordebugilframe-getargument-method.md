---
description: ': ICorDebugILFrame:: GetArgument Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugILFrame::GetArgument Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: c845f3c07502f3b1ce564833ee6ef98e3305463f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650527"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="b457a-103">ICorDebugILFrame::GetArgument Metodu</span><span class="sxs-lookup"><span data-stu-id="b457a-103">ICorDebugILFrame::GetArgument Method</span></span>

<span data-ttu-id="b457a-104">Bu Microsoft ara dili (MSIL) yığın çerçevesindeki belirtilen bağımsız değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b457a-104">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b457a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b457a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b457a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b457a-106">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="b457a-107">'ndaki Bu MSIL yığın çerçevesindeki bağımsız değişkenin dizini.</span><span class="sxs-lookup"><span data-stu-id="b457a-107">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="b457a-108">dışı Alınan değeri temsil eden ICorDebugValue nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b457a-108">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b457a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b457a-109">Remarks</span></span>  

 <span data-ttu-id="b457a-110">`GetArgument`Yöntemi, BIR MSIL yığın çerçevesinde veya tam zamanında (JIT) derlenmiş bir çerçevede kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b457a-110">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b457a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b457a-111">Requirements</span></span>  

 <span data-ttu-id="b457a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b457a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b457a-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b457a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b457a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b457a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b457a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b457a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

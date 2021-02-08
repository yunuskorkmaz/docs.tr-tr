---
description: ': ICorDebugILFrame:: CanSetIP yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugILFrame::CanSetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: d6ba0d073e8807ac6173f7f3e3982fe1d3eb4e01
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791445"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="b6a05-103">ICorDebugILFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b6a05-103">ICorDebugILFrame::CanSetIP Method</span></span>

<span data-ttu-id="b6a05-104">Microsoft ara dili (MSIL) kodunda belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="b6a05-104">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a05-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6a05-105">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6a05-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6a05-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="b6a05-107">'ndaki Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="b6a05-107">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6a05-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6a05-108">Remarks</span></span>  

 <span data-ttu-id="b6a05-109">`CanSetIP` [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) metodunu çağırmadan önce yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6a05-109">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="b6a05-110">`CanSetIP`S_OK dışında BIR HRESULT döndürürse, yine de çağırabilirsiniz `ICorDebugILFrame::SetIP` , ancak hata ayıklayıcının hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="b6a05-110">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6a05-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6a05-111">Requirements</span></span>  

 <span data-ttu-id="b6a05-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6a05-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6a05-113">**Üst bilgi:** CorDebug. IDL, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="b6a05-113">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="b6a05-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b6a05-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6a05-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6a05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

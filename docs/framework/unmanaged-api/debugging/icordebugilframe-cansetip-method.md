---
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
ms.openlocfilehash: 2bd4ab4a080461c56b0287d24aa288847445d803
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210325"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="f5fc8-102">ICorDebugILFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5fc8-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="f5fc8-103">Microsoft ara dili (MSIL) kodunda belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="f5fc8-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5fc8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5fc8-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5fc8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5fc8-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="f5fc8-106">'ndaki Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="f5fc8-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5fc8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5fc8-107">Remarks</span></span>  
 <span data-ttu-id="f5fc8-108">`CanSetIP` [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) metodunu çağırmadan önce yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5fc8-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="f5fc8-109">`CanSetIP`S_OK dışında BIR HRESULT döndürürse, yine de çağırabilirsiniz `ICorDebugILFrame::SetIP` , ancak hata ayıklayıcının hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="f5fc8-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5fc8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5fc8-110">Requirements</span></span>  
 <span data-ttu-id="f5fc8-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5fc8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5fc8-112">**Üst bilgi:** CorDebug. IDL, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="f5fc8-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="f5fc8-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5fc8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5fc8-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5fc8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

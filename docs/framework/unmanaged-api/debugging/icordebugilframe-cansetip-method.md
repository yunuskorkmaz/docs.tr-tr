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
ms.openlocfilehash: c6a02b080739d00667893008be4a19b4fa9a6ef2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788587"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="b42dc-102">ICorDebugILFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b42dc-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="b42dc-103">Microsoft ara dili (MSIL) kodunda belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="b42dc-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b42dc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b42dc-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b42dc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b42dc-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="b42dc-106">'ndaki Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="b42dc-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b42dc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b42dc-107">Remarks</span></span>  
 <span data-ttu-id="b42dc-108">[ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) metodunu çağırmadan önce `CanSetIP` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="b42dc-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="b42dc-109">`CanSetIP` S_OK dışında herhangi bir HRESULT döndürürse `ICorDebugILFrame::SetIP`yine de çağırabilirsiniz, ancak hata ayıklayıcının hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="b42dc-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b42dc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b42dc-110">Requirements</span></span>  
 <span data-ttu-id="b42dc-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b42dc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b42dc-112">**Üst bilgi:** CorDebug. IDL, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="b42dc-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="b42dc-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b42dc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b42dc-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b42dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
description: ': ICorDebugNativeFrame:: CanSetIP yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugNativeFrame::CanSetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: ec8f257b44143332063d7579b62dcc2afe0fccdd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637865"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="b7090-103">ICorDebugNativeFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7090-103">ICorDebugNativeFrame::CanSetIP Method</span></span>

<span data-ttu-id="b7090-104">Yerel koddaki belirtilen konum konumuna yönerge işaretçisini (IP) ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="b7090-104">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7090-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7090-105">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7090-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7090-106">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="b7090-107">'ndaki Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="b7090-107">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7090-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7090-108">Remarks</span></span>  

 <span data-ttu-id="b7090-109">`CanSetIP` [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) metodunu çağırmadan önce yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b7090-109">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="b7090-110">`CanSetIP`S_OK dışında BIR HRESULT döndürürse, yine de çağırabilirsiniz `ICorDebugNativeFrame::SetIP` , ancak hata ayıklayıcının hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="b7090-110">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7090-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7090-111">Requirements</span></span>  

 <span data-ttu-id="b7090-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7090-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7090-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b7090-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7090-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b7090-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7090-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7090-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7090-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7090-116">See also</span></span>

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad1ea4da252fe9fac89faa79195b6a6de245ad9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414706"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="80080-102">ICorDebugILFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80080-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="80080-103">Yönerge işaretçisi Microsoft Ara dili (MSIL) kodunu belirtilen uzaklık konumda ayarlamak güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="80080-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80080-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80080-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80080-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80080-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="80080-106">[in] Yönerge işaretçisi istenen ayarı.</span><span class="sxs-lookup"><span data-stu-id="80080-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80080-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80080-107">Remarks</span></span>  
 <span data-ttu-id="80080-108">Kullanım `CanSetIP` yöntemi çağırmadan önce [Icordebugılframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80080-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="80080-109">Varsa `CanSetIP` herhangi HRESULT döndürür S_OK dışında hala çağırabilirsiniz `ICorDebugILFrame::SetIP`, ancak hata ayıklayıcı ayıklanacak kod güvenli ve doğru yürütülmesi devam edecek garantisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="80080-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80080-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80080-110">Requirements</span></span>  
 <span data-ttu-id="80080-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80080-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80080-112">**Başlık:** CorDebug.idl, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="80080-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="80080-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80080-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80080-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80080-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

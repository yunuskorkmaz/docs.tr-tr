---
title: ICorDebugILFrame::EnumerateLocalVariables Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc9601105d05740e6db0a41bae521bd9a276d74
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471322"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="58ab6-102">ICorDebugILFrame::EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="58ab6-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="58ab6-103">Bir numaralandırıcı bu çerçevesinde yerel değişkenler için alır.</span><span class="sxs-lookup"><span data-stu-id="58ab6-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58ab6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58ab6-104">Syntax</span></span>  
  
```  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58ab6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58ab6-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="58ab6-106">[out] Yerel değişkenleri bu çerçevesi için Numaralandırıcı Icordebugvalueenum nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="58ab6-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58ab6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="58ab6-107">Remarks</span></span>  
 <span data-ttu-id="58ab6-108">`EnumerateLocalVariables` kullanılabilir bu Icordebugılframe nesnesi tarafından temsil edilen çağrı çerçevesinde yerel değişkenler listeleyen bir numaralandırıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="58ab6-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="58ab6-109">Bunlardan bazıları etkin olmayabilir çünkü liste çalışan işlevde harcanan, tüm yerel değişkenlerin içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="58ab6-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58ab6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58ab6-110">Requirements</span></span>  
 <span data-ttu-id="58ab6-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ab6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58ab6-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58ab6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58ab6-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58ab6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58ab6-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58ab6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

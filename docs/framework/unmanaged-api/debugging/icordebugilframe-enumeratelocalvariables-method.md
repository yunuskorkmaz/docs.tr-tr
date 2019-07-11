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
ms.openlocfilehash: c18f2fce23e979f27d9116e74b6c6b007cd33bf0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752893"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="676cc-102">ICorDebugILFrame::EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="676cc-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="676cc-103">Bir numaralandırıcı bu çerçevesinde yerel değişkenler için alır.</span><span class="sxs-lookup"><span data-stu-id="676cc-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="676cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="676cc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="676cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="676cc-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="676cc-106">[out] Yerel değişkenleri bu çerçevesi için Numaralandırıcı Icordebugvalueenum nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="676cc-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="676cc-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="676cc-107">Remarks</span></span>  
 <span data-ttu-id="676cc-108">`EnumerateLocalVariables` kullanılabilir bu Icordebugılframe nesnesi tarafından temsil edilen çağrı çerçevesinde yerel değişkenler listeleyen bir numaralandırıcıyı alır.</span><span class="sxs-lookup"><span data-stu-id="676cc-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="676cc-109">Bunlardan bazıları etkin olmayabilir çünkü liste çalışan işlevde harcanan, tüm yerel değişkenlerin içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="676cc-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="676cc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="676cc-110">Requirements</span></span>  
 <span data-ttu-id="676cc-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="676cc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="676cc-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="676cc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="676cc-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="676cc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="676cc-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="676cc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

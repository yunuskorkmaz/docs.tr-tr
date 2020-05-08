---
title: ICorDebugAppDomain::EnumerateBreakpoints Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
ms.openlocfilehash: bb994ae32c9e0e61c06c60521361a5c6c78d12fa
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895273"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="d2f3f-102">ICorDebugAppDomain::EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="d2f3f-103">Uygulama etki alanındaki tüm etkin kesme noktaları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2f3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2f3f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2f3f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2f3f-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="d2f3f-106">dışı Uygulama etki alanındaki tüm etkin kesme noktaları için numaralandırıcı olan ICorDebugBreakpointEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2f3f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2f3f-107">Remarks</span></span>  
 <span data-ttu-id="d2f3f-108">Numaralandırıcı, işlev kesme noktaları ve veri kesme noktaları da dahil olmak üzere tüm kesme noktaları türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d2f3f-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2f3f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2f3f-109">Requirements</span></span>  
 <span data-ttu-id="d2f3f-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2f3f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2f3f-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d2f3f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2f3f-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d2f3f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2f3f-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2f3f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

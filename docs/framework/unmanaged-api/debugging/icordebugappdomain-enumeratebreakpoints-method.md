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
ms.openlocfilehash: 3611684a17d51fc4fdba31dd4049540039b43e8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110515"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="a5a8c-102">ICorDebugAppDomain::EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5a8c-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="a5a8c-103">Uygulama etki alanındaki tüm etkin kesme noktaları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a5a8c-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5a8c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5a8c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5a8c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5a8c-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="a5a8c-106">dışı Uygulama etki alanındaki tüm etkin kesme noktaları için numaralandırıcı olan ICorDebugBreakpointEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5a8c-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5a8c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5a8c-107">Remarks</span></span>  
 <span data-ttu-id="a5a8c-108">Numaralandırıcı, işlev kesme noktaları ve veri kesme noktaları da dahil olmak üzere tüm kesme noktaları türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a5a8c-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5a8c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5a8c-109">Requirements</span></span>  
 <span data-ttu-id="a5a8c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5a8c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5a8c-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a5a8c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5a8c-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5a8c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5a8c-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5a8c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

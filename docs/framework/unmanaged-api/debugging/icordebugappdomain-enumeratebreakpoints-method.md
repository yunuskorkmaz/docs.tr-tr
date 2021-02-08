---
description: ': ICorDebugAppDomain:: Enumeratekesmenoktaları yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4bd9857b9c662bc76c7c9481f306b20e823e446f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772490"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="b3252-103">ICorDebugAppDomain::EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3252-103">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>

<span data-ttu-id="b3252-104">Uygulama etki alanındaki tüm etkin kesme noktaları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b3252-104">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3252-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3252-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3252-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3252-106">Parameters</span></span>  

 `ppBreakpoints`  
 <span data-ttu-id="b3252-107">dışı Uygulama etki alanındaki tüm etkin kesme noktaları için numaralandırıcı olan ICorDebugBreakpointEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b3252-107">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3252-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3252-108">Remarks</span></span>  

 <span data-ttu-id="b3252-109">Numaralandırıcı, işlev kesme noktaları ve veri kesme noktaları da dahil olmak üzere tüm kesme noktaları türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b3252-109">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3252-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3252-110">Requirements</span></span>  

 <span data-ttu-id="b3252-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3252-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3252-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b3252-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3252-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b3252-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3252-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3252-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

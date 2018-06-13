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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd7ee890a7f2c3ea8cd3de9fbe830575c0ca10c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402780"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="abfbe-102">ICorDebugAppDomain::EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abfbe-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="abfbe-103">Bir numaralandırıcı uygulama etki alanı için tüm etkin kesme noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="abfbe-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abfbe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abfbe-104">Syntax</span></span>  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abfbe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abfbe-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="abfbe-106">[out] Uygulama etki alanındaki tüm etkin kesme noktaları için Numaralandırıcı bir Icordebugbreakpointenum nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="abfbe-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abfbe-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abfbe-107">Remarks</span></span>  
 <span data-ttu-id="abfbe-108">Numaralayıcı kesme noktaları işlevi kesme noktaları ve veri kesme noktaları da dahil olmak üzere, tüm türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="abfbe-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abfbe-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abfbe-109">Requirements</span></span>  
 <span data-ttu-id="abfbe-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abfbe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abfbe-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abfbe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abfbe-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abfbe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abfbe-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abfbe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

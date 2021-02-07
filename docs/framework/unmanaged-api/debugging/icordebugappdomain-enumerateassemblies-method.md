---
description: ': ICorDebugAppDomain:: EnumerateAssemblies yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugAppDomain::EnumerateAssemblies Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateAssemblies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateAssemblies
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateAssemblies method [.NET Framework debugging]
- EnumerateAssemblies method [.NET Framework debugging]
ms.assetid: 7add64f9-19a8-46a9-be62-905d5e7d1bd8
topic_type:
- apiref
ms.openlocfilehash: 3ffa3180b80eac46e2d61019e4e4aa992f7c0e72
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754270"
---
# <a name="icordebugappdomainenumerateassemblies-method"></a><span data-ttu-id="6d9c6-103">ICorDebugAppDomain::EnumerateAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d9c6-103">ICorDebugAppDomain::EnumerateAssemblies Method</span></span>

<span data-ttu-id="6d9c6-104">Uygulama etki alanındaki derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="6d9c6-104">Gets an enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d9c6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d9c6-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateAssemblies (  
    [out] ICorDebugAssemblyEnum  **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d9c6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d9c6-106">Parameters</span></span>  

 `ppAssemblies`  
 <span data-ttu-id="6d9c6-107">dışı Uygulama etki alanındaki derlemelerin Numaralandırıcı olan ICorDebugAssemblyEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d9c6-107">[out] A pointer to the address of an ICorDebugAssemblyEnum object that is the enumerator for the assemblies in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d9c6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d9c6-108">Requirements</span></span>  

 <span data-ttu-id="6d9c6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d9c6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d9c6-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d9c6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d9c6-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6d9c6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d9c6-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d9c6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
description: ': ICorDebugAppDomain:: GetProcess metodu hakkında daha fazla bilgi edinin'
title: ICorDebugAppDomain::GetProcess Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type:
- apiref
ms.openlocfilehash: a681e58334df5dd7373e49b70c096fa1ff10773f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772412"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="63575-103">ICorDebugAppDomain::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="63575-103">ICorDebugAppDomain::GetProcess Method</span></span>

<span data-ttu-id="63575-104">Uygulama etki alanını içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="63575-104">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63575-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63575-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63575-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="63575-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="63575-107">dışı İşlemi temsil eden ICorDebugProcess nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="63575-107">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63575-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63575-108">Requirements</span></span>  

 <span data-ttu-id="63575-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63575-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63575-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63575-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63575-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="63575-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63575-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63575-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

---
description: ': ICorDebugModule:: GetProcess metodu hakkında daha fazla bilgi edinin'
title: ICorDebugModule::GetProcess Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetProcess method [.NET Framework debugging]
ms.assetid: 5e13446c-0271-446c-924a-9072c0e6eeae
topic_type:
- apiref
ms.openlocfilehash: eb8497ac8ec6913fe079d6f5f148d3769bf6633a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691633"
---
# <a name="icordebugmodulegetprocess-method"></a><span data-ttu-id="6d6a8-103">ICorDebugModule::GetProcess Metodu</span><span class="sxs-lookup"><span data-stu-id="6d6a8-103">ICorDebugModule::GetProcess Method</span></span>

<span data-ttu-id="6d6a8-104">Bu modülün bulunduğu işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="6d6a8-104">Gets the containing process of this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d6a8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d6a8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d6a8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d6a8-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="6d6a8-107">dışı Bu modülü içeren işlemi temsil eden bir ICorDebugProcess nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6d6a8-107">[out] A pointer to the address of an ICorDebugProcess object that represents the process containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d6a8-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d6a8-108">Requirements</span></span>  

 <span data-ttu-id="6d6a8-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d6a8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d6a8-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d6a8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d6a8-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6d6a8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d6a8-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d6a8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

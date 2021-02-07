---
description: ': ICorDebugFrame:: GetCode yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugFrame::GetCode Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type:
- apiref
ms.openlocfilehash: f45e0a29530a8b4ddbeaa92db4489a030ac1ae79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693037"
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="252d6-103">ICorDebugFrame::GetCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="252d6-103">ICorDebugFrame::GetCode Method</span></span>

<span data-ttu-id="252d6-104">Bu yığın çerçevesiyle ilişkili koda yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="252d6-104">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="252d6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="252d6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="252d6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="252d6-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="252d6-107">dışı Bu kareyle ilişkili kodu temsil eden bir ICorDebugCode nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="252d6-107">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="252d6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="252d6-108">Requirements</span></span>  

 <span data-ttu-id="252d6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="252d6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="252d6-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="252d6-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="252d6-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="252d6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="252d6-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="252d6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

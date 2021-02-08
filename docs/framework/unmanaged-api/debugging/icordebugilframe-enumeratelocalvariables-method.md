---
description: ': ICorDebugILFrame:: EnumerateLocalVariables yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 275cf7fcad32c452e6e7ebdd0774d64708a2398c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791393"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="5974a-103">ICorDebugILFrame::EnumerateLocalVariables Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5974a-103">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>

<span data-ttu-id="5974a-104">Bu çerçevedeki yerel değişkenler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5974a-104">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5974a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5974a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5974a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5974a-106">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="5974a-107">dışı Bu çerçevedeki yerel değişkenlerin numaralandırıcısı olan ICorDebugValueEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5974a-107">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5974a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5974a-108">Remarks</span></span>  

 <span data-ttu-id="5974a-109">`EnumerateLocalVariables` Bu ICorDebugILFrame nesnesi tarafından temsil edilen çağrı çerçevesinde kullanılabilen yerel değişkenleri listeleyerek bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5974a-109">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="5974a-110">Liste, çalışan işlevdeki tüm yerel değişkenleri içermeyebilir, çünkü bazıları etkin olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5974a-110">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5974a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5974a-111">Requirements</span></span>  

 <span data-ttu-id="5974a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5974a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5974a-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5974a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5974a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5974a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5974a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5974a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

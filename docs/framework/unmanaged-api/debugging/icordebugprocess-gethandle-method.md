---
description: ': ICorDebugProcess:: GetHandle Yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugProcess::GetHandle Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: fbc92be53b30d3c70f85fea36e05c6a5514b0f03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722132"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="51c5c-103">ICorDebugProcess::GetHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="51c5c-103">ICorDebugProcess::GetHandle Method</span></span>

<span data-ttu-id="51c5c-104">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="51c5c-104">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51c5c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51c5c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51c5c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51c5c-106">Parameters</span></span>  

 `phProcessHandle`  
 <span data-ttu-id="51c5c-107">dışı `HPROCESS` İşlemin tutamacı olan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="51c5c-107">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51c5c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51c5c-108">Remarks</span></span>  

 <span data-ttu-id="51c5c-109">Alınan tanıtıcı, hata ayıklama arabirimine aittir.</span><span class="sxs-lookup"><span data-stu-id="51c5c-109">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="51c5c-110">Hata ayıklayıcı, kullanılmadan önce tanıtıcıyı yinelememelidir.</span><span class="sxs-lookup"><span data-stu-id="51c5c-110">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51c5c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51c5c-111">Requirements</span></span>  

 <span data-ttu-id="51c5c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51c5c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51c5c-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51c5c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51c5c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51c5c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51c5c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51c5c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

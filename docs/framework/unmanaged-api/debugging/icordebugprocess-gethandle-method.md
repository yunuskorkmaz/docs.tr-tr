---
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
ms.openlocfilehash: 87b7b7381ef53f7e2abebc053b5c9f87f94d96c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695081"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="75828-102">ICorDebugProcess::GetHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="75828-102">ICorDebugProcess::GetHandle Method</span></span>

<span data-ttu-id="75828-103">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="75828-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75828-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="75828-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75828-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75828-105">Parameters</span></span>  

 `phProcessHandle`  
 <span data-ttu-id="75828-106">dışı `HPROCESS` İşlemin tutamacı olan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="75828-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75828-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75828-107">Remarks</span></span>  

 <span data-ttu-id="75828-108">Alınan tanıtıcı, hata ayıklama arabirimine aittir.</span><span class="sxs-lookup"><span data-stu-id="75828-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="75828-109">Hata ayıklayıcı, kullanılmadan önce tanıtıcıyı yinelememelidir.</span><span class="sxs-lookup"><span data-stu-id="75828-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75828-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75828-110">Requirements</span></span>  

 <span data-ttu-id="75828-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75828-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75828-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75828-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75828-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75828-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75828-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75828-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

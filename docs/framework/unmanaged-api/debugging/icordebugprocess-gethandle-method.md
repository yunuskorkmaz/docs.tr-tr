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
ms.openlocfilehash: ed7110cb2e2b7a91ed81d2d81c2989d1733c1ee6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207320"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="b1dc8-102">ICorDebugProcess::GetHandle Metodu</span><span class="sxs-lookup"><span data-stu-id="b1dc8-102">ICorDebugProcess::GetHandle Method</span></span>
<span data-ttu-id="b1dc8-103">İşlem için bir tanıtıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1dc8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1dc8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1dc8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1dc8-105">Parameters</span></span>  
 `phProcessHandle`  
 <span data-ttu-id="b1dc8-106">dışı `HPROCESS`İşlemin tutamacı olan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1dc8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b1dc8-107">Remarks</span></span>  
 <span data-ttu-id="b1dc8-108">Alınan tanıtıcı, hata ayıklama arabirimine aittir.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="b1dc8-109">Hata ayıklayıcı, kullanılmadan önce tanıtıcıyı yinelememelidir.</span><span class="sxs-lookup"><span data-stu-id="b1dc8-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1dc8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1dc8-110">Requirements</span></span>  
 <span data-ttu-id="b1dc8-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1dc8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1dc8-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1dc8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1dc8-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b1dc8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1dc8-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1dc8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

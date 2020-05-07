---
title: ICorDebugChain::EnumerateFrames Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: c8a62d8b4a4db0f36d991c32dbfc5bad68780f1b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894690"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="5c915-102">ICorDebugChain::EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c915-102">ICorDebugChain::EnumerateFrames Method</span></span>
<span data-ttu-id="5c915-103">En son kareyle başlayarak zincirdeki tüm yönetilen yığın çerçevelerini içeren bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="5c915-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c915-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c915-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c915-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c915-105">Parameters</span></span>  
 `ppFrames`  
 <span data-ttu-id="5c915-106">dışı Yığın çerçevelerinin Numaralandırıcı olan ICorDebugFrameEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5c915-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c915-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c915-107">Remarks</span></span>  
 <span data-ttu-id="5c915-108">Zincir, iş parçacığı için fiziksel çağrı yığınını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5c915-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="5c915-109">`EnumerateFrames` Yöntemi yalnızca yönetilen zincirler için çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c915-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="5c915-110">Hata ayıklama API 'SI, yönetilmeyen Zincirlerdeki çerçeveleri almak için yöntemler sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="5c915-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="5c915-111">Hata ayıklayıcı, bu bilgileri almak için diğer yolları kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5c915-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c915-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c915-112">Requirements</span></span>  
 <span data-ttu-id="5c915-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c915-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c915-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c915-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c915-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c915-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c915-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c915-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

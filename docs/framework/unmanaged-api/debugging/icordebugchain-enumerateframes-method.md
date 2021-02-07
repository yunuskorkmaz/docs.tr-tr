---
description: ': Icordebugzincirine:: EnumerateFrames metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 45bf69760eeccebada743d81e859a19e209b611a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711602"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="b03e4-103">ICorDebugChain::EnumerateFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b03e4-103">ICorDebugChain::EnumerateFrames Method</span></span>

<span data-ttu-id="b03e4-104">En son kareyle başlayarak zincirdeki tüm yönetilen yığın çerçevelerini içeren bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b03e4-104">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b03e4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b03e4-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b03e4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b03e4-106">Parameters</span></span>  

 `ppFrames`  
 <span data-ttu-id="b03e4-107">dışı Yığın çerçevelerinin Numaralandırıcı olan ICorDebugFrameEnum nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b03e4-107">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b03e4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b03e4-108">Remarks</span></span>  

 <span data-ttu-id="b03e4-109">Zincir, iş parçacığı için fiziksel çağrı yığınını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b03e4-109">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="b03e4-110">`EnumerateFrames`Yöntemi yalnızca yönetilen zincirler için çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b03e4-110">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="b03e4-111">Hata ayıklama API 'SI, yönetilmeyen Zincirlerdeki çerçeveleri almak için yöntemler sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b03e4-111">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="b03e4-112">Hata ayıklayıcı, bu bilgileri almak için diğer yolları kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b03e4-112">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b03e4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b03e4-113">Requirements</span></span>  

 <span data-ttu-id="b03e4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b03e4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b03e4-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b03e4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b03e4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b03e4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b03e4-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b03e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

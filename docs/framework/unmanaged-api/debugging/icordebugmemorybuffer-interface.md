---
title: ICorDebugMemoryBuffer Arabirimi
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 60f3b0c3230c524ca7d308d3cb80e50b0693715d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212340"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="ea271-102">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea271-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="ea271-103">Bellek içi arabelleği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ea271-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea271-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ea271-104">Methods</span></span>  
  
|<span data-ttu-id="ea271-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ea271-105">Method</span></span>|<span data-ttu-id="ea271-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea271-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea271-107">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea271-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="ea271-108">Bellek arabelleğinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="ea271-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="ea271-109">GetStartAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea271-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="ea271-110">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="ea271-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea271-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea271-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea271-112">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ea271-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ea271-113">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="ea271-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea271-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea271-114">Requirements</span></span>  
 <span data-ttu-id="ea271-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea271-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea271-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea271-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea271-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea271-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea271-118">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea271-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea271-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea271-119">See also</span></span>

- [<span data-ttu-id="ea271-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ea271-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ea271-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ea271-121">Debugging</span></span>](index.md)

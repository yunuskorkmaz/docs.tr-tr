---
description: ': ICorDebugMemoryBuffer arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugMemoryBuffer Arabirimi
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 94eeb0f31c0e1c053fabbd556768fa65dda2d328
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754023"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="94a4c-103">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94a4c-103">ICorDebugMemoryBuffer Interface</span></span>

<span data-ttu-id="94a4c-104">Bellek içi arabelleği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="94a4c-104">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94a4c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="94a4c-105">Methods</span></span>  
  
|<span data-ttu-id="94a4c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="94a4c-106">Method</span></span>|<span data-ttu-id="94a4c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94a4c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94a4c-108">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94a4c-108">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="94a4c-109">Bellek arabelleğinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="94a4c-109">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="94a4c-110">GetStartAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94a4c-110">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="94a4c-111">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="94a4c-111">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94a4c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94a4c-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94a4c-113">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94a4c-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="94a4c-114">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="94a4c-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94a4c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94a4c-115">Requirements</span></span>  

 <span data-ttu-id="94a4c-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94a4c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94a4c-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="94a4c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94a4c-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="94a4c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94a4c-119">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94a4c-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a4c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94a4c-120">See also</span></span>

- [<span data-ttu-id="94a4c-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94a4c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="94a4c-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="94a4c-122">Debugging</span></span>](index.md)

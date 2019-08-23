---
title: ICorDebugMemoryBuffer Arabirimi
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77fa6b1a8c7a559b9d88c0173e389ec11a75ec8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914781"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="8a8f1-102">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a8f1-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="8a8f1-103">Bellek içi arabelleği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8a8f1-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a8f1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a8f1-104">Methods</span></span>  
  
|<span data-ttu-id="8a8f1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8a8f1-105">Method</span></span>|<span data-ttu-id="8a8f1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a8f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a8f1-107">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a8f1-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="8a8f1-108">Bellek arabelleğinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="8a8f1-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="8a8f1-109">GetStartAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a8f1-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="8a8f1-110">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="8a8f1-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a8f1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a8f1-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a8f1-112">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8a8f1-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8a8f1-113">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="8a8f1-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a8f1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a8f1-114">Requirements</span></span>  
 <span data-ttu-id="8a8f1-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a8f1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a8f1-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8a8f1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a8f1-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8a8f1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a8f1-118">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a8f1-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a8f1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a8f1-119">See also</span></span>

- [<span data-ttu-id="8a8f1-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a8f1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8a8f1-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8a8f1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

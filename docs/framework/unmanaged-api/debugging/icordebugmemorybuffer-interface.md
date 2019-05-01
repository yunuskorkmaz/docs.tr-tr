---
title: ICorDebugMemoryBuffer Arabirimi
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e12b50e964ec470b843ae35c960f20c5675fd572
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955473"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="2a0bb-102">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a0bb-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="2a0bb-103">Bir bellek arabelleğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a0bb-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2a0bb-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2a0bb-104">Methods</span></span>  
  
|<span data-ttu-id="2a0bb-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2a0bb-105">Method</span></span>|<span data-ttu-id="2a0bb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a0bb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2a0bb-107">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a0bb-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="2a0bb-108">Bellek arabellek boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="2a0bb-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="2a0bb-109">GetStartAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a0bb-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="2a0bb-110">Bellek arabelleği başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="2a0bb-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a0bb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a0bb-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a0bb-112">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a0bb-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2a0bb-113">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="2a0bb-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a0bb-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a0bb-114">Requirements</span></span>  
 <span data-ttu-id="2a0bb-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a0bb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a0bb-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a0bb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a0bb-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a0bb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a0bb-118">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a0bb-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0bb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a0bb-119">See also</span></span>

- [<span data-ttu-id="2a0bb-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2a0bb-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2a0bb-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2a0bb-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

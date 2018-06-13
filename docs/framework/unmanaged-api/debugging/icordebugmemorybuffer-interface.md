---
title: ICorDebugMemoryBuffer arabirimi
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a1bc8e1206b8a82127645362cfe0a124074271c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414411"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="7bc34-102">ICorDebugMemoryBuffer arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bc34-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="7bc34-103">Bir bellek içi arabellek temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7bc34-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7bc34-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7bc34-104">Methods</span></span>  
  
|<span data-ttu-id="7bc34-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7bc34-105">Method</span></span>|<span data-ttu-id="7bc34-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bc34-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7bc34-107">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bc34-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="7bc34-108">Bellek arabellek boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="7bc34-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="7bc34-109">GetStartAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bc34-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="7bc34-110">Bellek arabelleği başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="7bc34-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bc34-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bc34-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bc34-112">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bc34-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="7bc34-113">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="7bc34-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bc34-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bc34-114">Requirements</span></span>  
 <span data-ttu-id="7bc34-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bc34-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bc34-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bc34-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bc34-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bc34-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bc34-118">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bc34-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bc34-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bc34-119">See Also</span></span>  
 [<span data-ttu-id="7bc34-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7bc34-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7bc34-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7bc34-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

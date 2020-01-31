---
title: ICorDebugMemoryBuffer Arabirimi
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: fa1bbca1e771cbc2b3475891862875b97b9e7f90
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793148"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="40887-102">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40887-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="40887-103">Bellek içi arabelleği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="40887-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40887-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="40887-104">Methods</span></span>  
  
|<span data-ttu-id="40887-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="40887-105">Method</span></span>|<span data-ttu-id="40887-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40887-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40887-107">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40887-107">GetSize Method</span></span>](icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="40887-108">Bellek arabelleğinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="40887-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="40887-109">GetStartAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40887-109">GetStartAddress Method</span></span>](icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="40887-110">Bellek arabelleğinin başlangıç adresini alır.</span><span class="sxs-lookup"><span data-stu-id="40887-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40887-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40887-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40887-112">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40887-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="40887-113">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="40887-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40887-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40887-114">Requirements</span></span>  
 <span data-ttu-id="40887-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40887-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40887-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40887-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40887-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40887-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40887-118">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40887-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40887-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40887-119">See also</span></span>

- [<span data-ttu-id="40887-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40887-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="40887-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="40887-121">Debugging</span></span>](index.md)

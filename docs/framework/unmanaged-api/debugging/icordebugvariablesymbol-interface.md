---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb2538894184c19bc107ce52cbef3ac86a97345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967976"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="08491-102">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08491-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="08491-103">Bir değişken için hata ayıklama sembol bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="08491-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="08491-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="08491-104">Methods</span></span>  
  
|<span data-ttu-id="08491-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="08491-105">Method</span></span>|<span data-ttu-id="08491-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08491-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="08491-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08491-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="08491-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="08491-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="08491-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08491-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="08491-110">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="08491-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="08491-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08491-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="08491-112">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="08491-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="08491-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08491-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="08491-114">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="08491-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="08491-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08491-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="08491-116">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="08491-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08491-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08491-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08491-118">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="08491-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="08491-119">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="08491-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08491-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08491-120">Requirements</span></span>  
 <span data-ttu-id="08491-121">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08491-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08491-122">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08491-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08491-123">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08491-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08491-124">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08491-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08491-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08491-125">See also</span></span>

- [<span data-ttu-id="08491-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08491-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="08491-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="08491-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugVariableSymbol arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a09fab1468435212c4437c58c113691e049b1ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="e9d32-102">ICorDebugVariableSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9d32-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="e9d32-103">Bir değişken için hata ayıklama sembol bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="e9d32-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9d32-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e9d32-104">Methods</span></span>  
  
|<span data-ttu-id="e9d32-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e9d32-105">Method</span></span>|<span data-ttu-id="e9d32-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9d32-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9d32-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9d32-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="e9d32-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="e9d32-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="e9d32-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9d32-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="e9d32-110">Bir değişken boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="e9d32-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="e9d32-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9d32-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="e9d32-112">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="e9d32-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="e9d32-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9d32-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="e9d32-114">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="e9d32-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="e9d32-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9d32-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="e9d32-116">Bir bayt dizisi değeri bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="e9d32-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9d32-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9d32-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9d32-118">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9d32-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e9d32-119">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="e9d32-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9d32-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9d32-120">Requirements</span></span>  
 <span data-ttu-id="e9d32-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9d32-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9d32-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9d32-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9d32-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9d32-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9d32-124">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9d32-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9d32-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9d32-125">See Also</span></span>  
 [<span data-ttu-id="e9d32-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e9d32-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e9d32-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e9d32-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

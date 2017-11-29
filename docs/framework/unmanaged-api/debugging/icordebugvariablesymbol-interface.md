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
ms.openlocfilehash: 89bae73e9dfb729e26f54dc7874418163870dc27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="21e97-102">ICorDebugVariableSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="21e97-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="21e97-103">Bir değişken için hata ayıklama sembol bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="21e97-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21e97-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="21e97-104">Methods</span></span>  
  
|<span data-ttu-id="21e97-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="21e97-105">Method</span></span>|<span data-ttu-id="21e97-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21e97-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21e97-107">GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e97-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="21e97-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="21e97-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="21e97-109">GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e97-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="21e97-110">Bir değişken boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="21e97-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="21e97-111">GetSlotIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e97-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="21e97-112">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="21e97-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="21e97-113">GetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e97-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="21e97-114">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="21e97-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="21e97-115">SetValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="21e97-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="21e97-116">Bir bayt dizisi değeri bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="21e97-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21e97-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21e97-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21e97-118">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="21e97-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="21e97-119">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="21e97-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e97-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21e97-120">Requirements</span></span>  
 <span data-ttu-id="21e97-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e97-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e97-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21e97-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21e97-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21e97-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21e97-124">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e97-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e97-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21e97-125">See Also</span></span>  
 [<span data-ttu-id="21e97-126">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="21e97-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="21e97-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="21e97-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

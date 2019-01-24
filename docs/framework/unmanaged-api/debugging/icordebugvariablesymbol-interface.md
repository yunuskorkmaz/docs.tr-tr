---
title: Icordebugvariablesymbol arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9822a3403c6ff738f7a6556a35cb383426575cb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582597"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="10ce5-102">Icordebugvariablesymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="10ce5-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="10ce5-103">Bir değişken için hata ayıklama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="10ce5-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10ce5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="10ce5-104">Methods</span></span>  
  
|<span data-ttu-id="10ce5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="10ce5-105">Method</span></span>|<span data-ttu-id="10ce5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10ce5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10ce5-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10ce5-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="10ce5-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="10ce5-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="10ce5-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10ce5-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="10ce5-110">Bir değişken boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="10ce5-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="10ce5-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10ce5-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="10ce5-112">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="10ce5-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="10ce5-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10ce5-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="10ce5-114">Bir bayt dizisi olarak bir değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="10ce5-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="10ce5-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10ce5-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="10ce5-116">Bir bayt dizisi değeri bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="10ce5-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10ce5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="10ce5-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10ce5-118">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10ce5-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="10ce5-119">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="10ce5-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10ce5-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10ce5-120">Requirements</span></span>  
 <span data-ttu-id="10ce5-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10ce5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10ce5-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10ce5-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10ce5-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10ce5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10ce5-124">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10ce5-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ce5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10ce5-125">See also</span></span>
- [<span data-ttu-id="10ce5-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="10ce5-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="10ce5-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="10ce5-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

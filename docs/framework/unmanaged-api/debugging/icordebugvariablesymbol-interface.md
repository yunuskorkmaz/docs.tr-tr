---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c7cdababd1e4b5fae4f5e48a654f861b708a6e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61930123"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="705de-102">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="705de-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="705de-103">Bir değişken için hata ayıklama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="705de-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="705de-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="705de-104">Methods</span></span>  
  
|<span data-ttu-id="705de-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="705de-105">Method</span></span>|<span data-ttu-id="705de-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="705de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="705de-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="705de-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="705de-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="705de-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="705de-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="705de-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="705de-110">Bir değişken boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="705de-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="705de-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="705de-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="705de-112">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="705de-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="705de-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="705de-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="705de-114">Bir bayt dizisi olarak bir değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="705de-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="705de-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="705de-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="705de-116">Bir bayt dizisi değeri bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="705de-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="705de-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="705de-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="705de-118">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="705de-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="705de-119">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="705de-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705de-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="705de-120">Requirements</span></span>  
 <span data-ttu-id="705de-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="705de-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705de-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="705de-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="705de-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="705de-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="705de-124">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="705de-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705de-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="705de-125">See also</span></span>

- [<span data-ttu-id="705de-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="705de-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="705de-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="705de-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

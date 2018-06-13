---
title: ICorDebugVariableSymbol arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73072dd9564853852b4d57e73c810680fdbcc4f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421343"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="70eb7-102">ICorDebugVariableSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="70eb7-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="70eb7-103">Bir değişken için hata ayıklama sembol bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="70eb7-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70eb7-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="70eb7-104">Methods</span></span>  
  
|<span data-ttu-id="70eb7-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="70eb7-105">Method</span></span>|<span data-ttu-id="70eb7-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="70eb7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70eb7-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70eb7-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="70eb7-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="70eb7-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="70eb7-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70eb7-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="70eb7-110">Bir değişken boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="70eb7-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="70eb7-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70eb7-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="70eb7-112">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="70eb7-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="70eb7-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70eb7-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="70eb7-114">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="70eb7-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="70eb7-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70eb7-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="70eb7-116">Bir bayt dizisi değeri bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="70eb7-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70eb7-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70eb7-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70eb7-118">Bu arabirim yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="70eb7-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="70eb7-119">Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.</span><span class="sxs-lookup"><span data-stu-id="70eb7-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70eb7-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70eb7-120">Requirements</span></span>  
 <span data-ttu-id="70eb7-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70eb7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70eb7-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70eb7-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70eb7-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70eb7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70eb7-124">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70eb7-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70eb7-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70eb7-125">See Also</span></span>  
 [<span data-ttu-id="70eb7-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="70eb7-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="70eb7-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="70eb7-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

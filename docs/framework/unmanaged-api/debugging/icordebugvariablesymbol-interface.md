---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c7cdababd1e4b5fae4f5e48a654f861b708a6e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226566"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="6412e-102">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6412e-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="6412e-103">Bir değişken için hata ayıklama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="6412e-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6412e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6412e-104">Methods</span></span>  
  
|<span data-ttu-id="6412e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6412e-105">Method</span></span>|<span data-ttu-id="6412e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6412e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6412e-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6412e-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="6412e-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="6412e-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="6412e-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6412e-109">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="6412e-110">Bir değişken boyutu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="6412e-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="6412e-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6412e-111">GetSlotIndex Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="6412e-112">Yerel bir değişken yönetilen yuvası dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="6412e-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="6412e-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6412e-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="6412e-114">Bir bayt dizisi olarak bir değişkenin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6412e-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="6412e-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6412e-115">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="6412e-116">Bir bayt dizisi değeri bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="6412e-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6412e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6412e-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6412e-118">Bu arabirim yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6412e-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6412e-119">Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="6412e-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6412e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6412e-120">Requirements</span></span>  
 <span data-ttu-id="6412e-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6412e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6412e-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6412e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6412e-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6412e-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6412e-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="6412e-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6412e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6412e-125">See also</span></span>

- [<span data-ttu-id="6412e-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6412e-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6412e-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6412e-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 9d17bc92dcae9e906dfe18d7665fbf489d278234
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790865"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="6e6aa-102">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e6aa-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="6e6aa-103">Bir değişken için hata ayıklama sembol bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e6aa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6e6aa-104">Methods</span></span>  
  
|<span data-ttu-id="6e6aa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6e6aa-105">Method</span></span>|<span data-ttu-id="6e6aa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e6aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e6aa-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e6aa-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="6e6aa-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="6e6aa-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e6aa-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="6e6aa-110">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="6e6aa-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e6aa-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="6e6aa-112">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="6e6aa-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e6aa-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="6e6aa-114">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="6e6aa-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e6aa-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="6e6aa-116">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e6aa-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e6aa-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e6aa-118">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="6e6aa-119">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e6aa-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e6aa-120">Requirements</span></span>  
 <span data-ttu-id="6e6aa-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e6aa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e6aa-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e6aa-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e6aa-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e6aa-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e6aa-124">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e6aa-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6aa-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e6aa-125">See also</span></span>

- [<span data-ttu-id="6e6aa-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6e6aa-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6e6aa-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6e6aa-127">Debugging</span></span>](index.md)

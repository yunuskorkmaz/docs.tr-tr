---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 412ecbfc03378947e5a578e163034d104718bc91
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397102"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="a9b82-102">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9b82-102">ICorDebugVariableSymbol Interface</span></span>
<span data-ttu-id="a9b82-103">Bir değişken için hata ayıklama sembol bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="a9b82-103">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9b82-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a9b82-104">Methods</span></span>  
  
|<span data-ttu-id="a9b82-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a9b82-105">Method</span></span>|<span data-ttu-id="a9b82-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9b82-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9b82-107">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9b82-107">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="a9b82-108">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="a9b82-108">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="a9b82-109">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9b82-109">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="a9b82-110">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="a9b82-110">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="a9b82-111">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9b82-111">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="a9b82-112">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="a9b82-112">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="a9b82-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9b82-113">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="a9b82-114">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="a9b82-114">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="a9b82-115">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9b82-115">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="a9b82-116">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="a9b82-116">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9b82-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9b82-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9b82-118">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a9b82-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a9b82-119">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="a9b82-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9b82-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9b82-120">Requirements</span></span>  
 <span data-ttu-id="a9b82-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9b82-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9b82-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a9b82-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9b82-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a9b82-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9b82-124">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9b82-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b82-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9b82-125">See also</span></span>

- [<span data-ttu-id="a9b82-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9b82-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a9b82-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a9b82-127">Debugging</span></span>](index.md)

---
description: ': ICorDebugVariableSymbol arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: fa3fc1f318627e9175a3066c3bd3eac00929ea60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790548"
---
# <a name="icordebugvariablesymbol-interface"></a><span data-ttu-id="0453c-103">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0453c-103">ICorDebugVariableSymbol Interface</span></span>

<span data-ttu-id="0453c-104">Bir değişken için hata ayıklama sembol bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="0453c-104">Retrieves the debug symbol information for a variable.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0453c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0453c-105">Methods</span></span>  
  
|<span data-ttu-id="0453c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0453c-106">Method</span></span>|<span data-ttu-id="0453c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0453c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0453c-108">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0453c-108">GetName Method</span></span>](icordebugvariablesymbol-getname-method.md)|<span data-ttu-id="0453c-109">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="0453c-109">Gets the name of a variable.</span></span>|  
|[<span data-ttu-id="0453c-110">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0453c-110">GetSize Method</span></span>](icordebugvariablesymbol-getsize-method.md)|<span data-ttu-id="0453c-111">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="0453c-111">Gets the size of a variable in bytes.</span></span>|  
|[<span data-ttu-id="0453c-112">GetSlotIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0453c-112">GetSlotIndex Method</span></span>](icordebugvariablesymbol-getslotindex-method.md)|<span data-ttu-id="0453c-113">Yerel bir değişkenin yönetilen yuva dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="0453c-113">Gets the managed slot index of a local variable.</span></span>|  
|[<span data-ttu-id="0453c-114">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0453c-114">GetValue Method</span></span>](icordebugvariablesymbol-getvalue-method.md)|<span data-ttu-id="0453c-115">Bir değişkenin değerini bir bayt dizisi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="0453c-115">Gets the value of a variable as a byte array.</span></span>|  
|[<span data-ttu-id="0453c-116">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0453c-116">SetValue Method</span></span>](icordebugvariablesymbol-setvalue-method.md)|<span data-ttu-id="0453c-117">Bir bayt dizisinin değerini bir değişkene atar.</span><span class="sxs-lookup"><span data-stu-id="0453c-117">Assigns the value of a byte array to a variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0453c-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0453c-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0453c-119">Bu arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0453c-119">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0453c-120">Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.</span><span class="sxs-lookup"><span data-stu-id="0453c-120">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0453c-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0453c-121">Requirements</span></span>  

 <span data-ttu-id="0453c-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0453c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0453c-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0453c-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0453c-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0453c-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0453c-125">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0453c-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0453c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0453c-126">See also</span></span>

- [<span data-ttu-id="0453c-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0453c-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0453c-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0453c-128">Debugging</span></span>](index.md)

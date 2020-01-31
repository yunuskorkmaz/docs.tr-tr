---
title: ICorDebugExceptionDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: 168ba2945608a5b26432c5a0f583e5d406f6ce9b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782825"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="88f46-102">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88f46-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="88f46-103">Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="88f46-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88f46-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="88f46-104">Methods</span></span>  
  
|<span data-ttu-id="88f46-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="88f46-105">Method</span></span>|<span data-ttu-id="88f46-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88f46-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="88f46-107">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88f46-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="88f46-108">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="88f46-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="88f46-109">GetNativeIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88f46-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="88f46-110">Bu özel durum ayıklama olayı için yerel arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="88f46-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="88f46-111">GetStackPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="88f46-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="88f46-112">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="88f46-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88f46-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88f46-113">Remarks</span></span>  
 <span data-ttu-id="88f46-114">`ICorDebugExceptionDebugEvent` arabirimi aşağıdaki olay türleri tarafından uygulanır:</span><span class="sxs-lookup"><span data-stu-id="88f46-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="88f46-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="88f46-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="88f46-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="88f46-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="88f46-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="88f46-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="88f46-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="88f46-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="88f46-119">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="88f46-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="88f46-120">Bir arabirim işaretçisini almak için `QueryInterface` çağırma girişimi, .NET Native dışındaki ICorDebug senaryoları için `E_NOINTERFACE` döndürür.</span><span class="sxs-lookup"><span data-stu-id="88f46-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88f46-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88f46-121">Requirements</span></span>  
 <span data-ttu-id="88f46-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88f46-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88f46-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="88f46-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88f46-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="88f46-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88f46-125">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88f46-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f46-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88f46-126">See also</span></span>

- [<span data-ttu-id="88f46-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="88f46-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="88f46-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="88f46-128">Debugging</span></span>](index.md)

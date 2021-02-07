---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugexceptiondebugger gevent arabirimi'
title: ICorDebugExceptionDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: eacaa344763fb77faef5f66282809d741f017b37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693427"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="508bf-103">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="508bf-103">ICorDebugExceptionDebugEvent Interface</span></span>

<span data-ttu-id="508bf-104">Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="508bf-104">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="508bf-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="508bf-105">Methods</span></span>  
  
|<span data-ttu-id="508bf-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="508bf-106">Method</span></span>|<span data-ttu-id="508bf-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="508bf-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="508bf-108">GetFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="508bf-108">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="508bf-109">Özel durumun yakalanıp yakalanamayacağını gösteren bir bayrak alır.</span><span class="sxs-lookup"><span data-stu-id="508bf-109">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="508bf-110">GetNativeIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="508bf-110">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="508bf-111">Bu özel durum ayıklama olayı için yerel arabirim işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="508bf-111">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="508bf-112">GetStackPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="508bf-112">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="508bf-113">Bu özel durum ayıklama olayının yığın işaretçisini alır.</span><span class="sxs-lookup"><span data-stu-id="508bf-113">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="508bf-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="508bf-114">Remarks</span></span>  

 <span data-ttu-id="508bf-115">`ICorDebugExceptionDebugEvent`Arabirim aşağıdaki olay türleri tarafından uygulanır:</span><span class="sxs-lookup"><span data-stu-id="508bf-115">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="508bf-116">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="508bf-116">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="508bf-117">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="508bf-117">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="508bf-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="508bf-118">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="508bf-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="508bf-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="508bf-120">Arabirim yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="508bf-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="508bf-121">`QueryInterface` `E_NOINTERFACE` .NET Native dışında ICorDebug senaryolarına yönelik bir arabirim işaretçisi alma çağrısı yapılmaya çalışılıyor.</span><span class="sxs-lookup"><span data-stu-id="508bf-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="508bf-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="508bf-122">Requirements</span></span>  

 <span data-ttu-id="508bf-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="508bf-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="508bf-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="508bf-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="508bf-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="508bf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="508bf-126">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="508bf-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="508bf-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="508bf-127">See also</span></span>

- [<span data-ttu-id="508bf-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="508bf-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="508bf-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="508bf-129">Debugging</span></span>](index.md)

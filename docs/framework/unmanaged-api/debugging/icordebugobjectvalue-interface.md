---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugObjectValue arabirimi'
title: ICorDebugObjectValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: a2af438bbb4c2f56eb1a72151e339b6b0a978eec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794781"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="79869-103">ICorDebugObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79869-103">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="79869-104">Bir nesnesi içeren bir değeri temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="79869-104">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79869-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="79869-105">Methods</span></span>  
  
|<span data-ttu-id="79869-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="79869-106">Method</span></span>|<span data-ttu-id="79869-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79869-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79869-108">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79869-108">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="79869-109"><xref:System.Type>Bu başvuruda bulunan nesnenin ortak dil çalışma zamanına (CLR) yönelik bir arabirim işaretçisi alır `ICorDebugObjectValue` .</span><span class="sxs-lookup"><span data-stu-id="79869-109">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="79869-110">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79869-110">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="79869-111">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="79869-111">Not implemented.</span></span>|  
|[<span data-ttu-id="79869-112">GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79869-112">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="79869-113">Belirtilen sınıftaki belirtilen alanın değerini temsil eden bir [ICorDebugValue](icordebugvalue-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="79869-113">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="79869-114">GetManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79869-114">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="79869-115">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="79869-115">Obsolete.</span></span> <span data-ttu-id="79869-116">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="79869-116">Do not call this method.</span></span>|  
|[<span data-ttu-id="79869-117">GetVirtualMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79869-117">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="79869-118">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="79869-118">Not implemented.</span></span>|  
|[<span data-ttu-id="79869-119">IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79869-119">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="79869-120">Bu nesnenin başvurduğu nesnenin bir değer türü olup olmadığını gösteren bir değer alır `ICorDebugObjectValue` .</span><span class="sxs-lookup"><span data-stu-id="79869-120">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="79869-121">SetFromManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79869-121">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="79869-122">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="79869-122">Obsolete.</span></span> <span data-ttu-id="79869-123">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="79869-123">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79869-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79869-124">Remarks</span></span>  

 <span data-ttu-id="79869-125">`ICorDebugObjectValue`Hata ayıklamakta olan işlem devam edene kadar geçerli kalır.</span><span class="sxs-lookup"><span data-stu-id="79869-125">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79869-126">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="79869-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79869-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79869-127">Requirements</span></span>  

 <span data-ttu-id="79869-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79869-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79869-129">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79869-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79869-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="79869-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79869-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79869-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79869-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79869-132">See also</span></span>

- [<span data-ttu-id="79869-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="79869-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

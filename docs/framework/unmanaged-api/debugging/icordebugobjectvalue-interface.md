---
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
ms.openlocfilehash: e104f8c522af2ee4cd42332b7459f4a2fd185511
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792684"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="f4398-102">ICorDebugObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4398-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="f4398-103">Bir nesnesi içeren bir değeri temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f4398-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4398-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f4398-104">Methods</span></span>  
  
|<span data-ttu-id="f4398-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f4398-105">Method</span></span>|<span data-ttu-id="f4398-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4398-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4398-107">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4398-107">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="f4398-108">Bu `ICorDebugObjectValue` başvurduğu nesnenin ortak dil çalışma zamanı (CLR) <xref:System.Type> için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f4398-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="f4398-109">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4398-109">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="f4398-110">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="f4398-110">Not implemented.</span></span>|  
|[<span data-ttu-id="f4398-111">GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4398-111">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="f4398-112">Belirtilen sınıftaki belirtilen alanın değerini temsil eden bir [ICorDebugValue](icordebugvalue-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f4398-112">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="f4398-113">GetManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4398-113">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="f4398-114">{1&gt;Artık kullanılmıyor.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f4398-114">Obsolete.</span></span> <span data-ttu-id="f4398-115">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="f4398-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="f4398-116">GetVirtualMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4398-116">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="f4398-117">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="f4398-117">Not implemented.</span></span>|  
|[<span data-ttu-id="f4398-118">IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4398-118">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="f4398-119">Bu `ICorDebugObjectValue` başvurduğu nesnenin bir değer türü olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f4398-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="f4398-120">SetFromManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4398-120">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="f4398-121">{1&gt;Artık kullanılmıyor.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f4398-121">Obsolete.</span></span> <span data-ttu-id="f4398-122">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="f4398-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4398-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4398-123">Remarks</span></span>  
 <span data-ttu-id="f4398-124">Hata ayıklamakta olan işlem devam edene kadar `ICorDebugObjectValue` geçerli kalır.</span><span class="sxs-lookup"><span data-stu-id="f4398-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4398-125">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f4398-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4398-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4398-126">Requirements</span></span>  
 <span data-ttu-id="f4398-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4398-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4398-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f4398-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4398-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f4398-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4398-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4398-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4398-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4398-131">See also</span></span>

- [<span data-ttu-id="f4398-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f4398-132">Debugging Interfaces</span></span>](debugging-interfaces.md)

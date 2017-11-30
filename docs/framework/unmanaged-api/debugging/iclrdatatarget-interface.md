---
title: ICLRDataTarget Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget
helpviewer_keywords: ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a40276b28f3d20428f0d7eb0556a762fdb56801
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="29055-102">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29055-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="29055-103">Ortak dil çalışma zamanı (CLR) hedef öğesinin etkileşim için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="29055-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29055-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="29055-104">Methods</span></span>  
  
|<span data-ttu-id="29055-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="29055-105">Method</span></span>|<span data-ttu-id="29055-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29055-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29055-107">Getcurrentthreadıd yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="29055-108">Geçerli iş parçacığı için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="29055-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="29055-109">Getımagebase yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="29055-110">Temel bellek adresi için belirtilen görüntü alır.</span><span class="sxs-lookup"><span data-stu-id="29055-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="29055-111">GetMachineType yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="29055-112">Hedef işlemin kullanarak yönerge kümesi türü için bir tanımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="29055-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="29055-113">GetPointerSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="29055-114">Bayt olarak geçerli hedefi bir işaretçi boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="29055-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="29055-115">GetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="29055-116">Bir işaretçi belirtilen tanımlayıcı ile iş parçacığı bağlamına alır.</span><span class="sxs-lookup"><span data-stu-id="29055-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="29055-117">GetTLSValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="29055-118">Belirtilen dizine belirtilen iş parçacığı için iş parçacığı yerel depolaması (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="29055-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="29055-119">ReadVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="29055-120">Verileri belirtilen sanal bellek adresinden belirtilen arabelleğe okur.</span><span class="sxs-lookup"><span data-stu-id="29055-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="29055-121">İstek yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="29055-122">Uygulama tarafından tanımlandığı şekilde, bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="29055-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="29055-123">SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="29055-124">Belirtilen iş parçacığı geçerli bağlamı hedef işleminde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="29055-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="29055-125">SetTLSValue yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="29055-126">Belirtilen iş parçacığının hedef işlemdeki iş parçacığı yerel depolaması (TLS) içinde bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="29055-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="29055-127">WriteVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="29055-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="29055-128">Verileri belirtilen arabelleğinden belirtilen sanal bellek adresi yazar.</span><span class="sxs-lookup"><span data-stu-id="29055-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29055-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29055-129">Remarks</span></span>  
 <span data-ttu-id="29055-130">API istemcisi (hata ayıklayıcı) belirli hedef öğesi için uygun şekilde bu arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="29055-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="29055-131">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="29055-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29055-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29055-132">Requirements</span></span>  
 <span data-ttu-id="29055-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29055-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29055-134">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="29055-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="29055-135">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29055-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29055-136">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29055-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29055-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29055-137">See Also</span></span>  
 [<span data-ttu-id="29055-138">Iclrdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="29055-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="29055-139">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="29055-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

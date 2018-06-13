---
title: ICLRDataTarget Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0a5abe8877c8414443fadc00e223df240721132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410448"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="693be-102">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="693be-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="693be-103">Ortak dil çalışma zamanı (CLR) hedef öğesinin etkileşim için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="693be-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="693be-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="693be-104">Methods</span></span>  
  
|<span data-ttu-id="693be-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="693be-105">Method</span></span>|<span data-ttu-id="693be-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="693be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="693be-107">GetCurrentThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="693be-108">Geçerli iş parçacığı için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="693be-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="693be-109">GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="693be-110">Temel bellek adresi için belirtilen görüntü alır.</span><span class="sxs-lookup"><span data-stu-id="693be-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="693be-111">GetMachineType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="693be-112">Hedef işlemin kullanarak yönerge kümesi türü için bir tanımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="693be-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="693be-113">GetPointerSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="693be-114">Bayt olarak geçerli hedefi bir işaretçi boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="693be-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="693be-115">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="693be-116">Bir işaretçi belirtilen tanımlayıcı ile iş parçacığı bağlamına alır.</span><span class="sxs-lookup"><span data-stu-id="693be-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="693be-117">GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="693be-118">Belirtilen dizine belirtilen iş parçacığı için iş parçacığı yerel depolaması (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="693be-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="693be-119">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="693be-120">Verileri belirtilen sanal bellek adresinden belirtilen arabelleğe okur.</span><span class="sxs-lookup"><span data-stu-id="693be-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="693be-121">Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="693be-122">Uygulama tarafından tanımlandığı şekilde, bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="693be-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="693be-123">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="693be-124">Belirtilen iş parçacığı geçerli bağlamı hedef işleminde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="693be-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="693be-125">SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="693be-126">Belirtilen iş parçacığının hedef işlemdeki iş parçacığı yerel depolaması (TLS) içinde bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="693be-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="693be-127">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="693be-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="693be-128">Verileri belirtilen arabelleğinden belirtilen sanal bellek adresi yazar.</span><span class="sxs-lookup"><span data-stu-id="693be-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="693be-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="693be-129">Remarks</span></span>  
 <span data-ttu-id="693be-130">API istemcisi (hata ayıklayıcı) belirli hedef öğesi için uygun şekilde bu arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="693be-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="693be-131">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="693be-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="693be-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="693be-132">Requirements</span></span>  
 <span data-ttu-id="693be-133">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="693be-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="693be-134">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="693be-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="693be-135">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="693be-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="693be-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="693be-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693be-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="693be-137">See Also</span></span>  
 [<span data-ttu-id="693be-138">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="693be-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="693be-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="693be-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

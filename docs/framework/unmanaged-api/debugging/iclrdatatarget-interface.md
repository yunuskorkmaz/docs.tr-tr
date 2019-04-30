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
ms.openlocfilehash: 6ed3cb62b56e80a7fe4ea54b43ac9f4a28b8d102
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698115"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="18925-102">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18925-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="18925-103">Bir hedef öğesi ortak dil çalışma zamanı (CLR) etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="18925-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18925-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="18925-104">Methods</span></span>  
  
|<span data-ttu-id="18925-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="18925-105">Method</span></span>|<span data-ttu-id="18925-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="18925-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18925-107">GetCurrentThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="18925-108">Geçerli iş parçacığı için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="18925-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="18925-109">GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="18925-110">Belirtilen görüntü için temel bir bellek adresi alır.</span><span class="sxs-lookup"><span data-stu-id="18925-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="18925-111">GetMachineType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="18925-112">Hedef işlemin kullandığı yönerge kümesi türü için bir tanımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="18925-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="18925-113">GetPointerSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="18925-114">Boyutu bayt cinsinden geçerli bir hedef için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="18925-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="18925-115">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="18925-116">Bir işaretçi belirtilen tanımlayıcı ile iş parçacığı için bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="18925-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="18925-117">GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="18925-118">Belirtilen dizindeki belirtilen iş parçacığı için iş parçacığı yerel depolaması (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="18925-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="18925-119">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="18925-120">Veri belirtilen sanal bellek adresinden belirtilen arabelleğe okur.</span><span class="sxs-lookup"><span data-stu-id="18925-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="18925-121">Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="18925-122">Uygulama tarafından tanımlanan bir işlemi istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="18925-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="18925-123">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="18925-124">Belirtilen iş parçacığının geçerli bağlam hedef işlemde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="18925-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="18925-125">SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="18925-126">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel depolama (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="18925-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="18925-127">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18925-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="18925-128">Verileri belirtilen arabellek belirtilen sanal bellek adresini yazar.</span><span class="sxs-lookup"><span data-stu-id="18925-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18925-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18925-129">Remarks</span></span>  
 <span data-ttu-id="18925-130">API istemcisi (diğer bir deyişle, hata ayıklayıcı) bu arabirimi belirli hedef öğe için uygun şekilde uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="18925-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="18925-131">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="18925-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18925-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18925-132">Requirements</span></span>  
 <span data-ttu-id="18925-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18925-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18925-134">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="18925-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="18925-135">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18925-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18925-136">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18925-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18925-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18925-137">See also</span></span>

- [<span data-ttu-id="18925-138">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18925-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="18925-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="18925-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

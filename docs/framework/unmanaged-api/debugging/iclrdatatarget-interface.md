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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100255"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="eb4c6-102">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="eb4c6-103">Bir hedef öğesi ortak dil çalışma zamanı (CLR) etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb4c6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="eb4c6-104">Methods</span></span>  
  
|<span data-ttu-id="eb4c6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="eb4c6-105">Method</span></span>|<span data-ttu-id="eb4c6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eb4c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb4c6-107">GetCurrentThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="eb4c6-108">Geçerli iş parçacığı için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="eb4c6-109">GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="eb4c6-110">Belirtilen görüntü için temel bir bellek adresi alır.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="eb4c6-111">GetMachineType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="eb4c6-112">Hedef işlemin kullandığı yönerge kümesi türü için bir tanımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="eb4c6-113">GetPointerSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="eb4c6-114">Boyutu bayt cinsinden geçerli bir hedef için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="eb4c6-115">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="eb4c6-116">Bir işaretçi belirtilen tanımlayıcı ile iş parçacığı için bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="eb4c6-117">GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="eb4c6-118">Belirtilen dizindeki belirtilen iş parçacığı için iş parçacığı yerel depolaması (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="eb4c6-119">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="eb4c6-120">Veri belirtilen sanal bellek adresinden belirtilen arabelleğe okur.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="eb4c6-121">Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="eb4c6-122">Uygulama tarafından tanımlanan bir işlemi istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="eb4c6-123">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="eb4c6-124">Belirtilen iş parçacığının geçerli bağlam hedef işlemde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="eb4c6-125">SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="eb4c6-126">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel depolama (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="eb4c6-127">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="eb4c6-128">Verileri belirtilen arabellek belirtilen sanal bellek adresini yazar.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb4c6-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb4c6-129">Remarks</span></span>  
 <span data-ttu-id="eb4c6-130">API istemcisi (diğer bir deyişle, hata ayıklayıcı) bu arabirimi belirli hedef öğe için uygun şekilde uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="eb4c6-131">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb4c6-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb4c6-132">Requirements</span></span>  
 <span data-ttu-id="eb4c6-133">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb4c6-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb4c6-134">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="eb4c6-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="eb4c6-135">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb4c6-135">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="eb4c6-136">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="eb4c6-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eb4c6-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb4c6-137">See also</span></span>

- [<span data-ttu-id="eb4c6-138">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb4c6-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="eb4c6-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb4c6-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
description: 'Bu konuda daha fazla bilgi edinin: ICLRDataTarget arabirimi'
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
ms.openlocfilehash: f24760f638705a1bde7e055069cbc3a18a0896fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738227"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="21f69-103">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21f69-103">ICLRDataTarget Interface</span></span>

<span data-ttu-id="21f69-104">Ortak dil çalışma zamanının (CLR) hedef öğesiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="21f69-104">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21f69-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="21f69-105">Methods</span></span>  
  
|<span data-ttu-id="21f69-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="21f69-106">Method</span></span>|<span data-ttu-id="21f69-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21f69-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21f69-108">GetCurrentThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-108">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="21f69-109">Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="21f69-109">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="21f69-110">GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-110">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="21f69-111">Belirtilen görüntü için taban bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="21f69-111">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="21f69-112">GetMachineType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-112">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="21f69-113">Hedef işlemin kullandığı yönerge kümesi türü için bir tanımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="21f69-113">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="21f69-114">GetPointerSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-114">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="21f69-115">Geçerli hedefin bir işaretçisinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="21f69-115">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="21f69-116">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-116">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="21f69-117">Belirtilen tanımlayıcıya sahip iş parçacığı bağlamına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="21f69-117">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="21f69-118">GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-118">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="21f69-119">Belirtilen iş parçacığı için belirtilen dizindeki iş parçacığı yerel depolaması 'nda (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="21f69-119">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="21f69-120">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-120">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="21f69-121">Belirtilen sanal bellek adresinden belirtilen arabelleğe verileri okur.</span><span class="sxs-lookup"><span data-stu-id="21f69-121">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="21f69-122">Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-122">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="21f69-123">Uygulama tarafından tanımlanan bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="21f69-123">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="21f69-124">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-124">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="21f69-125">Hedef işlemde belirtilen iş parçacığının geçerli bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="21f69-125">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="21f69-126">SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-126">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="21f69-127">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel deposunda (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="21f69-127">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="21f69-128">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21f69-128">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="21f69-129">Belirtilen arabellekteki verileri belirtilen sanal bellek adresine yazar.</span><span class="sxs-lookup"><span data-stu-id="21f69-129">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21f69-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21f69-130">Remarks</span></span>  

 <span data-ttu-id="21f69-131">API istemcisi (diğer bir deyişle, hata ayıklayıcı), bu arabirimin belirli bir hedef öğe için uygun şekilde uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="21f69-131">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="21f69-132">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="21f69-132">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f69-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21f69-133">Requirements</span></span>  

 <span data-ttu-id="21f69-134">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21f69-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f69-135">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="21f69-135">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="21f69-136">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21f69-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21f69-137">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f69-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f69-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21f69-138">See also</span></span>

- [<span data-ttu-id="21f69-139">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21f69-139">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="21f69-140">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="21f69-140">Debugging Interfaces</span></span>](debugging-interfaces.md)

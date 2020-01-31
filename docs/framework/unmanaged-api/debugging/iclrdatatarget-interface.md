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
ms.openlocfilehash: 2b5c99e40aabdbc654bdc612729b2756e3ef5bb4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793710"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="96a7a-102">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96a7a-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="96a7a-103">Ortak dil çalışma zamanının (CLR) hedef öğesiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="96a7a-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96a7a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="96a7a-104">Methods</span></span>  
  
|<span data-ttu-id="96a7a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="96a7a-105">Method</span></span>|<span data-ttu-id="96a7a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96a7a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96a7a-107">GetCurrentThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-107">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="96a7a-108">Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="96a7a-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="96a7a-109">GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-109">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="96a7a-110">Belirtilen görüntü için taban bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="96a7a-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="96a7a-111">GetMachineType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-111">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="96a7a-112">Hedef işlemin kullandığı yönerge kümesi türü için bir tanımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="96a7a-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="96a7a-113">GetPointerSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-113">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="96a7a-114">Geçerli hedefin bir işaretçisinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="96a7a-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="96a7a-115">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-115">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="96a7a-116">Belirtilen tanımlayıcıya sahip iş parçacığı bağlamına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="96a7a-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="96a7a-117">GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-117">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="96a7a-118">Belirtilen iş parçacığı için belirtilen dizindeki iş parçacığı yerel depolaması 'nda (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="96a7a-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="96a7a-119">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-119">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="96a7a-120">Belirtilen sanal bellek adresinden belirtilen arabelleğe verileri okur.</span><span class="sxs-lookup"><span data-stu-id="96a7a-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="96a7a-121">Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-121">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="96a7a-122">Uygulama tarafından tanımlanan bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="96a7a-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="96a7a-123">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-123">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="96a7a-124">Hedef işlemde belirtilen iş parçacığının geçerli bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="96a7a-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="96a7a-125">SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-125">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="96a7a-126">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel deposunda (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="96a7a-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="96a7a-127">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96a7a-127">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="96a7a-128">Belirtilen arabellekteki verileri belirtilen sanal bellek adresine yazar.</span><span class="sxs-lookup"><span data-stu-id="96a7a-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96a7a-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96a7a-129">Remarks</span></span>  
 <span data-ttu-id="96a7a-130">API istemcisi (diğer bir deyişle, hata ayıklayıcı), bu arabirimin belirli bir hedef öğe için uygun şekilde uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="96a7a-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="96a7a-131">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="96a7a-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96a7a-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96a7a-132">Requirements</span></span>  
 <span data-ttu-id="96a7a-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96a7a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96a7a-134">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="96a7a-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="96a7a-135">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="96a7a-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96a7a-136">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96a7a-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a7a-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96a7a-137">See also</span></span>

- [<span data-ttu-id="96a7a-138">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96a7a-138">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="96a7a-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="96a7a-139">Debugging Interfaces</span></span>](debugging-interfaces.md)

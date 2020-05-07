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
ms.openlocfilehash: 30806394a8895084068acaec6f7d03c6b67bb14b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860573"
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="b695b-102">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b695b-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="b695b-103">Ortak dil çalışma zamanının (CLR) hedef öğesiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b695b-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b695b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b695b-104">Methods</span></span>  
  
|<span data-ttu-id="b695b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b695b-105">Method</span></span>|<span data-ttu-id="b695b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b695b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b695b-107">GetCurrentThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-107">GetCurrentThreadID Method</span></span>](iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="b695b-108">Geçerli iş parçacığının işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="b695b-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="b695b-109">GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-109">GetImageBase Method</span></span>](iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="b695b-110">Belirtilen görüntü için taban bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="b695b-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="b695b-111">GetMachineType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-111">GetMachineType Method</span></span>](iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="b695b-112">Hedef işlemin kullandığı yönerge kümesi türü için bir tanımlayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="b695b-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="b695b-113">GetPointerSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-113">GetPointerSize Method</span></span>](iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="b695b-114">Geçerli hedefin bir işaretçisinin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="b695b-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="b695b-115">GetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-115">GetThreadContext Method</span></span>](iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="b695b-116">Belirtilen tanımlayıcıya sahip iş parçacığı bağlamına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="b695b-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="b695b-117">GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-117">GetTLSValue Method</span></span>](iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="b695b-118">Belirtilen iş parçacığı için belirtilen dizindeki iş parçacığı yerel depolaması 'nda (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b695b-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="b695b-119">ReadVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-119">ReadVirtual Method</span></span>](iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="b695b-120">Belirtilen sanal bellek adresinden belirtilen arabelleğe verileri okur.</span><span class="sxs-lookup"><span data-stu-id="b695b-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="b695b-121">Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-121">Request Method</span></span>](iclrdatatarget-request-method.md)|<span data-ttu-id="b695b-122">Uygulama tarafından tanımlanan bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="b695b-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="b695b-123">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-123">SetThreadContext Method</span></span>](iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="b695b-124">Hedef işlemde belirtilen iş parçacığının geçerli bağlamını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b695b-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="b695b-125">SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-125">SetTLSValue Method</span></span>](iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="b695b-126">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel deposunda (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b695b-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="b695b-127">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b695b-127">WriteVirtual Method</span></span>](iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="b695b-128">Belirtilen arabellekteki verileri belirtilen sanal bellek adresine yazar.</span><span class="sxs-lookup"><span data-stu-id="b695b-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b695b-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b695b-129">Remarks</span></span>  
 <span data-ttu-id="b695b-130">API istemcisi (diğer bir deyişle, hata ayıklayıcı), bu arabirimin belirli bir hedef öğe için uygun şekilde uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b695b-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="b695b-131">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="b695b-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b695b-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b695b-132">Requirements</span></span>  
 <span data-ttu-id="b695b-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b695b-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b695b-134">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b695b-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b695b-135">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b695b-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b695b-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b695b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b695b-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b695b-137">See also</span></span>

- [<span data-ttu-id="b695b-138">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b695b-138">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="b695b-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b695b-139">Debugging Interfaces</span></span>](debugging-interfaces.md)

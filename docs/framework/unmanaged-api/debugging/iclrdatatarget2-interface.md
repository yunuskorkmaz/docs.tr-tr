---
title: ICLRDataTarget2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45f16fd50880b5d2482be365f3c55e1427cc6eaa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701007"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="b4749-102">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4749-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="b4749-103">Öğesinin [Iclrdatatarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) , veri erişim Hizmetleri düzeyi tarafından hedef işlemde sanal bellek bölümlerini işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b4749-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4749-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b4749-104">Methods</span></span>  
  
|<span data-ttu-id="b4749-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b4749-105">Method</span></span>|<span data-ttu-id="b4749-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4749-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4749-107">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4749-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="b4749-108">Hedef işlemin adres alanında bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="b4749-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="b4749-109">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4749-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="b4749-110">Hedef işlemin adres alanında daha önce ayrılmış bellek kazandırır.</span><span class="sxs-lookup"><span data-stu-id="b4749-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4749-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4749-111">Remarks</span></span>  
 <span data-ttu-id="b4749-112">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="b4749-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="b4749-113">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="b4749-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="b4749-114">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4749-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4749-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4749-115">Requirements</span></span>  
 <span data-ttu-id="b4749-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4749-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4749-117">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="b4749-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b4749-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4749-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4749-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4749-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4749-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4749-120">See also</span></span>
- [<span data-ttu-id="b4749-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4749-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="b4749-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b4749-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

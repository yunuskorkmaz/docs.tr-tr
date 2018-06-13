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
ms.openlocfilehash: 6fc26694bded2c7df1a53a96e8743f3be73c93eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408510"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="73393-102">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73393-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="73393-103">Öğesinin bir alt [Iclrdatatarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) , veri erişim Hizmetleri katmanı tarafından hedef işlem sanal bellek bölgelerde işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73393-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73393-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="73393-104">Methods</span></span>  
  
|<span data-ttu-id="73393-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="73393-105">Method</span></span>|<span data-ttu-id="73393-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73393-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73393-107">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73393-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="73393-108">Hedef işlemin adres alanındaki bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="73393-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="73393-109">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="73393-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="73393-110">Hedef işlemin adres alanında daha önce ayrılmış bellek boşaltır.</span><span class="sxs-lookup"><span data-stu-id="73393-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73393-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73393-111">Remarks</span></span>  
 <span data-ttu-id="73393-112">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="73393-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="73393-113">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="73393-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="73393-114">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="73393-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73393-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="73393-115">Requirements</span></span>  
 <span data-ttu-id="73393-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73393-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73393-117">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="73393-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="73393-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73393-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73393-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73393-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73393-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73393-120">See Also</span></span>  
 [<span data-ttu-id="73393-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="73393-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="73393-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="73393-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

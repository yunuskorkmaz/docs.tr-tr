---
description: 'Daha fazla bilgi edinin: ICLRDataTarget2 Interface'
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
ms.openlocfilehash: 9ba6d11ea043d3b6ba85544b47e063f585854af8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794851"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="f197b-103">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f197b-103">ICLRDataTarget2 Interface</span></span>

<span data-ttu-id="f197b-104">Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan [ICLRDataTarget](iclrdatatarget-interface.md) 'nin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f197b-104">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f197b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f197b-105">Methods</span></span>  
  
|<span data-ttu-id="f197b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f197b-106">Method</span></span>|<span data-ttu-id="f197b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f197b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f197b-108">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f197b-108">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="f197b-109">Hedef işlemin adres alanında belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="f197b-109">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="f197b-110">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f197b-110">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="f197b-111">Hedef işlemin adres alanında daha önce ayrılan belleği boşaltır.</span><span class="sxs-lookup"><span data-stu-id="f197b-111">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f197b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f197b-112">Remarks</span></span>  

 <span data-ttu-id="f197b-113">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="f197b-113">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="f197b-114">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="f197b-114">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="f197b-115">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f197b-115">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f197b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f197b-116">Requirements</span></span>  

 <span data-ttu-id="f197b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f197b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f197b-118">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="f197b-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f197b-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f197b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f197b-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f197b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f197b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f197b-121">See also</span></span>

- [<span data-ttu-id="f197b-122">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f197b-122">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="f197b-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f197b-123">Debugging Interfaces</span></span>](debugging-interfaces.md)

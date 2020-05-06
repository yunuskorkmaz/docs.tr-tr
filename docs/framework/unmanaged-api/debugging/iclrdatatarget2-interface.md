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
ms.openlocfilehash: 6b2700b2f12e312f06640a06e5ec82fbc58f2ca9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860466"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="d25bf-102">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d25bf-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="d25bf-103">Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan [ICLRDataTarget](iclrdatatarget-interface.md) 'nin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d25bf-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d25bf-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d25bf-104">Methods</span></span>  
  
|<span data-ttu-id="d25bf-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d25bf-105">Method</span></span>|<span data-ttu-id="d25bf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d25bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d25bf-107">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d25bf-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="d25bf-108">Hedef işlemin adres alanında belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="d25bf-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="d25bf-109">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d25bf-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="d25bf-110">Hedef işlemin adres alanında daha önce ayrılan belleği boşaltır.</span><span class="sxs-lookup"><span data-stu-id="d25bf-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d25bf-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d25bf-111">Remarks</span></span>  
 <span data-ttu-id="d25bf-112">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="d25bf-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="d25bf-113">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="d25bf-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="d25bf-114">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="d25bf-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d25bf-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d25bf-115">Requirements</span></span>  
 <span data-ttu-id="d25bf-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d25bf-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d25bf-117">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="d25bf-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d25bf-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d25bf-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d25bf-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d25bf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d25bf-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d25bf-120">See also</span></span>

- [<span data-ttu-id="d25bf-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d25bf-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="d25bf-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d25bf-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

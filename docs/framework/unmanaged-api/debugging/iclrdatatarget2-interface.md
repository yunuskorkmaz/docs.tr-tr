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
ms.openlocfilehash: bdc8378a129dd5bb1d9fdcb080c7b5cd53d34091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789069"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="ad53a-102">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad53a-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="ad53a-103">Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan [ICLRDataTarget](iclrdatatarget-interface.md) 'nin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ad53a-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad53a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ad53a-104">Methods</span></span>  
  
|<span data-ttu-id="ad53a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ad53a-105">Method</span></span>|<span data-ttu-id="ad53a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad53a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad53a-107">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad53a-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="ad53a-108">Hedef işlemin adres alanında belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="ad53a-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="ad53a-109">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad53a-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="ad53a-110">Hedef işlemin adres alanında daha önce ayrılan belleği boşaltır.</span><span class="sxs-lookup"><span data-stu-id="ad53a-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad53a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad53a-111">Remarks</span></span>  
 <span data-ttu-id="ad53a-112">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="ad53a-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="ad53a-113">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="ad53a-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="ad53a-114">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad53a-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad53a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad53a-115">Requirements</span></span>  
 <span data-ttu-id="ad53a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad53a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad53a-117">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ad53a-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ad53a-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ad53a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad53a-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad53a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad53a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad53a-120">See also</span></span>

- [<span data-ttu-id="ad53a-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad53a-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="ad53a-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad53a-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

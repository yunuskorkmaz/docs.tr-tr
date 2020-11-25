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
ms.openlocfilehash: dee5108439610b67c3397cebcd8ee5f84d4eacea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723642"
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="63f2c-102">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63f2c-102">ICLRDataTarget2 Interface</span></span>

<span data-ttu-id="63f2c-103">Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan [ICLRDataTarget](iclrdatatarget-interface.md) 'nin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="63f2c-103">A subclass of [ICLRDataTarget](iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63f2c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="63f2c-104">Methods</span></span>  
  
|<span data-ttu-id="63f2c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="63f2c-105">Method</span></span>|<span data-ttu-id="63f2c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63f2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63f2c-107">AllocVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63f2c-107">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="63f2c-108">Hedef işlemin adres alanında belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="63f2c-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="63f2c-109">FreeVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63f2c-109">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="63f2c-110">Hedef işlemin adres alanında daha önce ayrılan belleği boşaltır.</span><span class="sxs-lookup"><span data-stu-id="63f2c-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63f2c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63f2c-111">Remarks</span></span>  

 <span data-ttu-id="63f2c-112">API istemcisi (yani hata ayıklayıcı) bu arabirimi belirli hedef işlem için uygun şekilde yürütmelidir.</span><span class="sxs-lookup"><span data-stu-id="63f2c-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="63f2c-113">Örneğin, canlı bir işlem bir bellek dökümününkinden farklı bir yürütmeye sahip olur.</span><span class="sxs-lookup"><span data-stu-id="63f2c-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="63f2c-114">Hedef, kendi bellek bölümlerinin değiştirilmesini desteklemiyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="63f2c-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63f2c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63f2c-115">Requirements</span></span>  

 <span data-ttu-id="63f2c-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63f2c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63f2c-117">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="63f2c-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="63f2c-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="63f2c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63f2c-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63f2c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63f2c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63f2c-120">See also</span></span>

- [<span data-ttu-id="63f2c-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63f2c-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="63f2c-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="63f2c-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

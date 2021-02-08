---
description: 'Daha fazla bilgi edinin: ICLRGCManager2 Interface'
title: ICLRGCManager2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: 455b3a99d10fa43bf325e9f7075d255dd55ae38b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789963"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="bf0d0-103">ICLRGCManager2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf0d0-103">ICLRGCManager2 Interface</span></span>

<span data-ttu-id="bf0d0-104">Bir konağın ortak dil çalışma zamanının çöp toplama sistemiyle etkileşime geçmesini sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bf0d0-104">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf0d0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bf0d0-105">Methods</span></span>  
  
|<span data-ttu-id="bf0d0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bf0d0-106">Method</span></span>|<span data-ttu-id="bf0d0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf0d0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf0d0-108">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf0d0-108">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="bf0d0-109">Çöp toplama kesiminin boyutunu ve çöp toplama sisteminin oluşturma 0 ' nın en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="bf0d0-109">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="bf0d0-110">1. nesil ve kesim boyutlarını daha büyük olarak sunar `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="bf0d0-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf0d0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf0d0-111">Remarks</span></span>  

 <span data-ttu-id="bf0d0-112">Bu arabirim [ICLRGCManager arabiriminden](iclrgcmanager-interface.md)devralır.</span><span class="sxs-lookup"><span data-stu-id="bf0d0-112">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="bf0d0-113">Ortak dil çalışma zamanı (CLR), kendi çöp toplama mekanizmasını yönetilen türle uygular <xref:System.GC> .</span><span class="sxs-lookup"><span data-stu-id="bf0d0-113">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="bf0d0-114">Çöp toplama sistemi hakkında daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf0d0-114">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf0d0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf0d0-115">Requirements</span></span>  

 <span data-ttu-id="bf0d0-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf0d0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf0d0-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bf0d0-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf0d0-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="bf0d0-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf0d0-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf0d0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf0d0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf0d0-120">See also</span></span>

- [<span data-ttu-id="bf0d0-121">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="bf0d0-121">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="bf0d0-122">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="bf0d0-122">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="bf0d0-123">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf0d0-123">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="bf0d0-124">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bf0d0-124">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="bf0d0-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bf0d0-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="bf0d0-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="bf0d0-126">Hosting</span></span>](index.md)

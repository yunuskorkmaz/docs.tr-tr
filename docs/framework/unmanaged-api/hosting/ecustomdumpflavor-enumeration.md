---
title: ECustomDumpFlavor Numaralandırması
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
ms.openlocfilehash: 1b8440ed6e878aac3dd08d9f8ed528c93739a724
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686325"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="dfac8-102">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="dfac8-102">ECustomDumpFlavor Enumeration</span></span>

<span data-ttu-id="dfac8-103">Hataları bildirirken yığın dökümünün özel bir alt kümesine hangi öğelerin ekleneceğini belirten değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="dfac8-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfac8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="dfac8-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="dfac8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dfac8-105">Members</span></span>  
  
|<span data-ttu-id="dfac8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="dfac8-106">Member</span></span>|<span data-ttu-id="dfac8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfac8-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="dfac8-108">Özel yığın dökümünün bir mini döküm olarak başlaması gerektiğini ve aynı yönteme geçirilen tüm [Customdumpitem](customdumpitem-structure.md) örnekleri tarafından belirtilen ek verileri dahil edileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfac8-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="dfac8-109">Özel yığın dökümünden dinamik olarak ayrılmamış tüm çalışma zamanı durum verilerini toplaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="dfac8-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfac8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfac8-110">Remarks</span></span>  

 <span data-ttu-id="dfac8-111">`ECustomDumpFlavor` [Ilrerrorreportingmanager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) metoduna türünde bir parametre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="dfac8-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfac8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfac8-112">Requirements</span></span>  

 <span data-ttu-id="dfac8-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfac8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfac8-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dfac8-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfac8-115">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfac8-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfac8-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfac8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfac8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfac8-117">See also</span></span>

- [<span data-ttu-id="dfac8-118">ECustomDumpItemKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="dfac8-118">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="dfac8-119">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfac8-119">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="dfac8-120">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="dfac8-120">Hosting Enumerations</span></span>](hosting-enumerations.md)

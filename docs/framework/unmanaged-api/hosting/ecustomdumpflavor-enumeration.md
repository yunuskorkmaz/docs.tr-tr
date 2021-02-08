---
description: 'Daha fazla bilgi edinin: ECustomDumpFlavor numaralandırması'
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
ms.openlocfilehash: 3ef118368fc827472bdaacb0b03d8c2011275056
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785539"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="b7fa8-103">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b7fa8-103">ECustomDumpFlavor Enumeration</span></span>

<span data-ttu-id="b7fa8-104">Hataları bildirirken yığın dökümünün özel bir alt kümesine hangi öğelerin ekleneceğini belirten değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="b7fa8-104">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fa8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7fa8-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="b7fa8-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b7fa8-106">Members</span></span>  
  
|<span data-ttu-id="b7fa8-107">Üye</span><span class="sxs-lookup"><span data-stu-id="b7fa8-107">Member</span></span>|<span data-ttu-id="b7fa8-108">Description</span><span class="sxs-lookup"><span data-stu-id="b7fa8-108">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="b7fa8-109">Özel yığın dökümünün bir mini döküm olarak başlaması gerektiğini ve aynı yönteme geçirilen tüm [Customdumpitem](customdumpitem-structure.md) örnekleri tarafından belirtilen ek verileri dahil edileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7fa8-109">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="b7fa8-110">Özel yığın dökümünden dinamik olarak ayrılmamış tüm çalışma zamanı durum verilerini toplaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b7fa8-110">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7fa8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b7fa8-111">Remarks</span></span>  

 <span data-ttu-id="b7fa8-112">`ECustomDumpFlavor` [Ilrerrorreportingmanager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) metoduna türünde bir parametre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="b7fa8-112">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7fa8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7fa8-113">Requirements</span></span>  

 <span data-ttu-id="b7fa8-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7fa8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7fa8-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b7fa8-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7fa8-116">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7fa8-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7fa8-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7fa8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fa8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7fa8-118">See also</span></span>

- [<span data-ttu-id="b7fa8-119">ECustomDumpItemKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b7fa8-119">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="b7fa8-120">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7fa8-120">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="b7fa8-121">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="b7fa8-121">Hosting Enumerations</span></span>](hosting-enumerations.md)

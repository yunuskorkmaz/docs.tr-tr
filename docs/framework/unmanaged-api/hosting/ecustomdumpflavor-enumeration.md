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
ms.openlocfilehash: 9b4c1187945b4c243375a3096c3a8a3b22599aef
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616287"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="99dac-102">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="99dac-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="99dac-103">Hataları bildirirken yığın dökümünün özel bir alt kümesine hangi öğelerin ekleneceğini belirten değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="99dac-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99dac-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="99dac-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="99dac-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="99dac-105">Members</span></span>  
  
|<span data-ttu-id="99dac-106">Üye</span><span class="sxs-lookup"><span data-stu-id="99dac-106">Member</span></span>|<span data-ttu-id="99dac-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99dac-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="99dac-108">Özel yığın dökümünün bir mini döküm olarak başlaması gerektiğini ve aynı yönteme geçirilen tüm [Customdumpitem](customdumpitem-structure.md) örnekleri tarafından belirtilen ek verileri dahil edileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="99dac-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="99dac-109">Özel yığın dökümünden dinamik olarak ayrılmamış tüm çalışma zamanı durum verilerini toplaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="99dac-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99dac-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99dac-110">Remarks</span></span>  
 <span data-ttu-id="99dac-111">`ECustomDumpFlavor` [Ilrerrorreportingmanager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) metoduna türünde bir parametre geçirilir.</span><span class="sxs-lookup"><span data-stu-id="99dac-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99dac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99dac-112">Requirements</span></span>  
 <span data-ttu-id="99dac-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99dac-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99dac-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="99dac-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99dac-115">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="99dac-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99dac-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99dac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99dac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99dac-117">See also</span></span>

- [<span data-ttu-id="99dac-118">ECustomDumpItemKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="99dac-118">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="99dac-119">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99dac-119">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="99dac-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="99dac-120">Hosting Enumerations</span></span>](hosting-enumerations.md)

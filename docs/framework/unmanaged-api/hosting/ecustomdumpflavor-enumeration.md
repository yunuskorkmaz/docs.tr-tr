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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2be9f112d5997ec8a6b126229eb8608eb8dd8520
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627648"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="21ee7-102">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="21ee7-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="21ee7-103">Hataları bildirirken hangi öğelerin bir yığının özel alt kümesinde içerecek şekilde dökümü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="21ee7-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21ee7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21ee7-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="21ee7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="21ee7-105">Members</span></span>  
  
|<span data-ttu-id="21ee7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="21ee7-106">Member</span></span>|<span data-ttu-id="21ee7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21ee7-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="21ee7-108">Özel yığının döküm ve bir mini döküm Başlat tarafından belirtilen ek verileri dahil etmek belirtir [Customdumpıtem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri aynı yönteme geçirilen.</span><span class="sxs-lookup"><span data-stu-id="21ee7-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="21ee7-109">Özel yığının döküm dinamik olarak ayrılmamış tüm çalışma zamanı durumu verilerini toplamanız gereken belirtir.</span><span class="sxs-lookup"><span data-stu-id="21ee7-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21ee7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21ee7-110">Remarks</span></span>  
 <span data-ttu-id="21ee7-111">Türünde bir parametre `ECustomDumpFlavor` geçirilir [Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="21ee7-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21ee7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21ee7-112">Requirements</span></span>  
 <span data-ttu-id="21ee7-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21ee7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21ee7-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21ee7-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21ee7-115">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="21ee7-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21ee7-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21ee7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ee7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21ee7-117">See also</span></span>
- [<span data-ttu-id="21ee7-118">ECustomDumpItemKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="21ee7-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="21ee7-119">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21ee7-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="21ee7-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="21ee7-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

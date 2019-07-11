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
ms.openlocfilehash: a416a51f5121f29d373fcfdfa6b0597d9b10ded5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779386"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="17750-102">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="17750-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="17750-103">Hataları bildirirken hangi öğelerin bir yığının özel alt kümesinde içerecek şekilde dökümü gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="17750-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17750-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17750-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="17750-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="17750-105">Members</span></span>  
  
|<span data-ttu-id="17750-106">Üye</span><span class="sxs-lookup"><span data-stu-id="17750-106">Member</span></span>|<span data-ttu-id="17750-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17750-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="17750-108">Özel yığının döküm ve bir mini döküm Başlat tarafından belirtilen ek verileri dahil etmek belirtir [Customdumpıtem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri aynı yönteme geçirilen.</span><span class="sxs-lookup"><span data-stu-id="17750-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="17750-109">Özel yığının döküm dinamik olarak ayrılmamış tüm çalışma zamanı durumu verilerini toplamanız gereken belirtir.</span><span class="sxs-lookup"><span data-stu-id="17750-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17750-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17750-110">Remarks</span></span>  
 <span data-ttu-id="17750-111">Türünde bir parametre `ECustomDumpFlavor` geçirilir [Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="17750-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17750-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17750-112">Requirements</span></span>  
 <span data-ttu-id="17750-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17750-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17750-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="17750-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17750-115">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17750-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17750-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17750-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17750-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17750-117">See also</span></span>

- [<span data-ttu-id="17750-118">ECustomDumpItemKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="17750-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="17750-119">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17750-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="17750-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="17750-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

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
ms.openlocfilehash: 057794fe524a0ee01f6f090ca7e11a4a4b523047
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124924"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="fe97c-102">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fe97c-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="fe97c-103">Hataları bildirirken yığın dökümünün özel bir alt kümesine hangi öğelerin ekleneceğini belirten değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="fe97c-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe97c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe97c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="fe97c-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fe97c-105">Members</span></span>  
  
|<span data-ttu-id="fe97c-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fe97c-106">Member</span></span>|<span data-ttu-id="fe97c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe97c-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="fe97c-108">Özel yığın dökümünün bir mini döküm olarak başlaması gerektiğini ve aynı yönteme geçirilen tüm [Customdumpitem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) örnekleri tarafından belirtilen ek verileri dahil edileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe97c-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="fe97c-109">Özel yığın dökümünden dinamik olarak ayrılmamış tüm çalışma zamanı durum verilerini toplaması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="fe97c-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe97c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe97c-110">Remarks</span></span>  
 <span data-ttu-id="fe97c-111">`ECustomDumpFlavor` türünde bir parametre [ICLRErrorReportingManager:: BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="fe97c-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe97c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe97c-112">Requirements</span></span>  
 <span data-ttu-id="fe97c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe97c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe97c-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fe97c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe97c-115">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fe97c-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe97c-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe97c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe97c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe97c-117">See also</span></span>

- [<span data-ttu-id="fe97c-118">ECustomDumpItemKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="fe97c-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="fe97c-119">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe97c-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="fe97c-120">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fe97c-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

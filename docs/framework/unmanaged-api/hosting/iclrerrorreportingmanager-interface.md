---
title: ICLRErrorReportingManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a20b79dd5eda9c431511cc49e7e3adaa9486b2aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155993"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="7d446-102">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7d446-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="7d446-103">Özel yığının dökümlerinde hata raporlama yapılandırmak konak izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d446-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d446-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7d446-104">Methods</span></span>  
  
|<span data-ttu-id="7d446-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7d446-105">Method</span></span>|<span data-ttu-id="7d446-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d446-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d446-107">BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d446-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="7d446-108">Hata bildirimi için özel bir yığın dökümlerini yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d446-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="7d446-109">EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d446-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="7d446-110">Önceki bir çağrı tarafından ayarlanan özel yığının döküm yapılandırmasını temizler `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="7d446-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="7d446-111">GetBucketParametersForCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7d446-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="7d446-112">Watson demet çağıran iş parçacığında geçerli özel durumu alır.</span><span class="sxs-lookup"><span data-stu-id="7d446-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d446-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d446-113">Remarks</span></span>  
 <span data-ttu-id="7d446-114">`BeginCustomDump` Yöntemi özel yığının döküm yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7d446-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="7d446-115">`EndCustomDump` Yöntemi özel yığının döküm yapılandırmasını temizler ve herhangi bir ilişkili durumu serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="7d446-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="7d446-116">Özel döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d446-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7d446-117">Aranacak hata `EndCustomDump` bellek sızıntısı neden olur.</span><span class="sxs-lookup"><span data-stu-id="7d446-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d446-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7d446-118">Requirements</span></span>  
 <span data-ttu-id="7d446-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d446-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d446-120">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d446-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d446-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7d446-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7d446-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="7d446-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d446-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d446-123">See also</span></span>

- [<span data-ttu-id="7d446-124">ECustomDumpItemKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7d446-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="7d446-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7d446-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

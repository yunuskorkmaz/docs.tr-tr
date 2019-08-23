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
ms.openlocfilehash: 2a9d9cff0360e4eb27584fe0f22c1c20396ff8f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966254"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="ebfb6-102">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebfb6-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="ebfb6-103">Ana bilgisayarın hata raporlaması için özel yığın dökümleri yapılandırmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebfb6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ebfb6-104">Methods</span></span>  
  
|<span data-ttu-id="ebfb6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ebfb6-105">Method</span></span>|<span data-ttu-id="ebfb6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebfb6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebfb6-107">BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebfb6-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="ebfb6-108">Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="ebfb6-109">EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebfb6-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="ebfb6-110">Daha önceki bir çağrısıyla `BeginCustomDump`ayarlanan özel yığın dökümü yapılandırmasını temizler.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="ebfb6-111">GetBucketParametersForCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebfb6-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="ebfb6-112">Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebfb6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ebfb6-113">Remarks</span></span>  
 <span data-ttu-id="ebfb6-114">Yöntemi `BeginCustomDump` , özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="ebfb6-115">`EndCustomDump` Yöntemi, özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="ebfb6-116">Özel döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ebfb6-117">Çağırma `EndCustomDump` hatası, belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebfb6-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebfb6-118">Requirements</span></span>  
 <span data-ttu-id="ebfb6-119">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebfb6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebfb6-120">**Üst bilgi** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ebfb6-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebfb6-121">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ebfb6-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebfb6-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebfb6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfb6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebfb6-123">See also</span></span>

- [<span data-ttu-id="ebfb6-124">ECustomDumpItemKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="ebfb6-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="ebfb6-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ebfb6-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

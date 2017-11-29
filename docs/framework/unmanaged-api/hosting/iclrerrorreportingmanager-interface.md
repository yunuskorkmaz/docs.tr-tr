---
title: ICLRErrorReportingManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager
helpviewer_keywords: ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590cd87d6a566e9c8c3819fd1b250997938e9c35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="e3492-102">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3492-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="e3492-103">Hata bildirimi için özel yığın dökümleri yapılandırmak konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3492-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3492-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e3492-104">Methods</span></span>  
  
|<span data-ttu-id="e3492-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e3492-105">Method</span></span>|<span data-ttu-id="e3492-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3492-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3492-107">BeginCustomDump yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3492-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="e3492-108">Hata bildirimi için özel yığın dökümleri yapılandırılmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e3492-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="e3492-109">EndCustomDump yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3492-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="e3492-110">Önceki bir çağrı tarafından ayarlanan özel yığın dökümü yapılandırması temizler `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="e3492-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="e3492-111">GetBucketParametersForCurrentException yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3492-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="e3492-112">Geçerli özel durumun çağıran iş parçacığı üzerinde Watson demet alır.</span><span class="sxs-lookup"><span data-stu-id="e3492-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3492-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3492-113">Remarks</span></span>  
 <span data-ttu-id="e3492-114">`BeginCustomDump` Yöntemi özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e3492-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="e3492-115">`EndCustomDump` Yöntemi özel yığın dökümü yapılandırması temizler ve tüm ilişkili durumu boşaltır.</span><span class="sxs-lookup"><span data-stu-id="e3492-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="e3492-116">Özel döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e3492-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3492-117">Çağrılacak hatası `EndCustomDump` bellek sızıntısı neden olur.</span><span class="sxs-lookup"><span data-stu-id="e3492-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3492-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3492-118">Requirements</span></span>  
 <span data-ttu-id="e3492-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3492-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3492-120">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3492-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3492-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e3492-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3492-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3492-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3492-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3492-123">See Also</span></span>  
 [<span data-ttu-id="e3492-124">Ecustomdumpıtemkind numaralandırması</span><span class="sxs-lookup"><span data-stu-id="e3492-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="e3492-125">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e3492-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

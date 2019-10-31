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
ms.openlocfilehash: 49a60b6b9b076138d8ff1f8a15041e9a6bacfede
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129248"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="b5071-102">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5071-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="b5071-103">Ana bilgisayarın hata raporlaması için özel yığın dökümleri yapılandırmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5071-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b5071-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b5071-104">Methods</span></span>  
  
|<span data-ttu-id="b5071-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b5071-105">Method</span></span>|<span data-ttu-id="b5071-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5071-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5071-107">BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5071-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="b5071-108">Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5071-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="b5071-109">EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5071-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="b5071-110">Daha önceki bir `BeginCustomDump`çağrısıyla ayarlanan özel yığın dökümü yapılandırmasını temizler.</span><span class="sxs-lookup"><span data-stu-id="b5071-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="b5071-111">GetBucketParametersForCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5071-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="b5071-112">Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.</span><span class="sxs-lookup"><span data-stu-id="b5071-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5071-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5071-113">Remarks</span></span>  
 <span data-ttu-id="b5071-114">`BeginCustomDump` yöntemi özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b5071-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="b5071-115">`EndCustomDump` yöntemi, özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="b5071-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="b5071-116">Özel döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5071-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b5071-117">`EndCustomDump` çağıramaması, belleğin sızmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b5071-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5071-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5071-118">Requirements</span></span>  
 <span data-ttu-id="b5071-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5071-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5071-120">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b5071-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b5071-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b5071-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5071-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5071-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5071-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5071-123">See also</span></span>

- [<span data-ttu-id="b5071-124">ECustomDumpItemKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b5071-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="b5071-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b5071-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

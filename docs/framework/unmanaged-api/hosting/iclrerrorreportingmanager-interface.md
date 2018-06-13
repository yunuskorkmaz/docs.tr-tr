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
ms.openlocfilehash: bf9e04ed1d3a68fed120c4c13ad992af1f777244
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433802"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="485f0-102">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="485f0-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="485f0-103">Hata bildirimi için özel yığın dökümleri yapılandırmak konak izin yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="485f0-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="485f0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="485f0-104">Methods</span></span>  
  
|<span data-ttu-id="485f0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="485f0-105">Method</span></span>|<span data-ttu-id="485f0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="485f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="485f0-107">BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="485f0-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="485f0-108">Hata bildirimi için özel yığın dökümleri yapılandırılmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="485f0-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="485f0-109">EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="485f0-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="485f0-110">Önceki bir çağrı tarafından ayarlanan özel yığın dökümü yapılandırması temizler `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="485f0-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="485f0-111">GetBucketParametersForCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="485f0-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="485f0-112">Geçerli özel durumun çağıran iş parçacığı üzerinde Watson demet alır.</span><span class="sxs-lookup"><span data-stu-id="485f0-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="485f0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="485f0-113">Remarks</span></span>  
 <span data-ttu-id="485f0-114">`BeginCustomDump` Yöntemi özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="485f0-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="485f0-115">`EndCustomDump` Yöntemi özel yığın dökümü yapılandırması temizler ve tüm ilişkili durumu boşaltır.</span><span class="sxs-lookup"><span data-stu-id="485f0-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="485f0-116">Özel döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="485f0-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="485f0-117">Çağrılacak hatası `EndCustomDump` bellek sızıntısı neden olur.</span><span class="sxs-lookup"><span data-stu-id="485f0-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="485f0-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="485f0-118">Requirements</span></span>  
 <span data-ttu-id="485f0-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="485f0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="485f0-120">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="485f0-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="485f0-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="485f0-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="485f0-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="485f0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="485f0-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="485f0-123">See Also</span></span>  
 [<span data-ttu-id="485f0-124">ECustomDumpItemKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="485f0-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="485f0-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="485f0-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

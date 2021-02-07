---
description: ': ICLRErrorReportingManager arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 094fe52858983fd0e1e5826e823932cb150b6087
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689280"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="9c1b6-103">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c1b6-103">ICLRErrorReportingManager Interface</span></span>

<span data-ttu-id="9c1b6-104">Ana bilgisayarın hata raporlaması için özel yığın dökümleri yapılandırmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c1b6-104">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9c1b6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9c1b6-105">Methods</span></span>  
  
|<span data-ttu-id="9c1b6-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9c1b6-106">Method</span></span>|<span data-ttu-id="9c1b6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9c1b6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9c1b6-108">BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c1b6-108">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="9c1b6-109">Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9c1b6-109">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="9c1b6-110">EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c1b6-110">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="9c1b6-111">Daha önceki bir çağrısıyla ayarlanan özel yığın dökümü yapılandırmasını temizler `BeginCustomDump` .</span><span class="sxs-lookup"><span data-stu-id="9c1b6-111">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="9c1b6-112">GetBucketParametersForCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c1b6-112">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="9c1b6-113">Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.</span><span class="sxs-lookup"><span data-stu-id="9c1b6-113">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c1b6-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c1b6-114">Remarks</span></span>  

 <span data-ttu-id="9c1b6-115">`BeginCustomDump`Yöntemi, özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9c1b6-115">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="9c1b6-116">`EndCustomDump`Yöntemi, özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="9c1b6-116">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="9c1b6-117">Özel döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9c1b6-117">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9c1b6-118">Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c1b6-118">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c1b6-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c1b6-119">Requirements</span></span>  

 <span data-ttu-id="9c1b6-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c1b6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c1b6-121">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9c1b6-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9c1b6-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9c1b6-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c1b6-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c1b6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1b6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c1b6-124">See also</span></span>

- [<span data-ttu-id="9c1b6-125">ECustomDumpItemKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9c1b6-125">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="9c1b6-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9c1b6-126">Hosting Interfaces</span></span>](hosting-interfaces.md)

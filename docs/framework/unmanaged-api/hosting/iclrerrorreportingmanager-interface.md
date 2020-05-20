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
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617002"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="cf18d-102">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf18d-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="cf18d-103">Ana bilgisayarın hata raporlaması için özel yığın dökümleri yapılandırmasına izin veren yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf18d-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf18d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cf18d-104">Methods</span></span>  
  
|<span data-ttu-id="cf18d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cf18d-105">Method</span></span>|<span data-ttu-id="cf18d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf18d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cf18d-107">BeginCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf18d-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="cf18d-108">Hata raporlama için özel yığın dökümlerinin yapılandırmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf18d-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="cf18d-109">EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf18d-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="cf18d-110">Daha önceki bir çağrısıyla ayarlanan özel yığın dökümü yapılandırmasını temizler `BeginCustomDump` .</span><span class="sxs-lookup"><span data-stu-id="cf18d-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="cf18d-111">GetBucketParametersForCurrentException Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf18d-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="cf18d-112">Çağıran iş parçacığında geçerli özel durumun Watson demetini alır.</span><span class="sxs-lookup"><span data-stu-id="cf18d-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf18d-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf18d-113">Remarks</span></span>  
 <span data-ttu-id="cf18d-114">`BeginCustomDump`Yöntemi, özel yığın dökümü yapılandırmasını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf18d-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="cf18d-115">`EndCustomDump`Yöntemi, özel yığın dökümü yapılandırmasını temizler ve ilişkili tüm durumları serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="cf18d-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="cf18d-116">Özel döküm tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf18d-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cf18d-117">Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf18d-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf18d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf18d-118">Requirements</span></span>  
 <span data-ttu-id="cf18d-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf18d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf18d-120">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cf18d-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf18d-121">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cf18d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf18d-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf18d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf18d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf18d-123">See also</span></span>

- [<span data-ttu-id="cf18d-124">ECustomDumpItemKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="cf18d-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="cf18d-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cf18d-125">Hosting Interfaces</span></span>](hosting-interfaces.md)

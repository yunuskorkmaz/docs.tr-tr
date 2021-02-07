---
description: ': ICLRErrorReportingManager:: EndCustomDump yöntemi hakkında daha fazla bilgi edinin'
title: ICLRErrorReportingManager::EndCustomDump Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 406d7d77f4cd63c69fec56acb0819d56c6271630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689475"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="f401d-103">ICLRErrorReportingManager::EndCustomDump Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f401d-103">ICLRErrorReportingManager::EndCustomDump Method</span></span>

<span data-ttu-id="f401d-104">Daha önceki bir çağrıda belirtilen özel yığın dökümü yapılandırmasını [ICLRErrorReportingManager:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) metoduna kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f401d-104">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f401d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f401d-105">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f401d-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f401d-106">Return Value</span></span>  
  
|<span data-ttu-id="f401d-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f401d-107">HRESULT</span></span>|<span data-ttu-id="f401d-108">Description</span><span class="sxs-lookup"><span data-stu-id="f401d-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f401d-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f401d-109">S_OK</span></span>|<span data-ttu-id="f401d-110">`EndCustomDump` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f401d-110">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="f401d-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f401d-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f401d-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f401d-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f401d-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f401d-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f401d-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f401d-114">The call timed out.</span></span>|  
|<span data-ttu-id="f401d-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f401d-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f401d-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f401d-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f401d-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f401d-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f401d-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f401d-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f401d-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f401d-119">E_FAIL</span></span>|<span data-ttu-id="f401d-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f401d-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f401d-121">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f401d-121">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f401d-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f401d-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f401d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f401d-123">Remarks</span></span>  

 <span data-ttu-id="f401d-124">`EndCustomDump`Yöntemi, yöntemi için daha önceki bir çağrı tarafından ayarlanan özel yığın dökümü yapılandırmasını temizler `BeginCustomDump` ve ilişkili tüm durumları boşaltır.</span><span class="sxs-lookup"><span data-stu-id="f401d-124">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="f401d-125">Özel yığın dökümü tamamlandıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f401d-125">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f401d-126">Çağırma hatası, `EndCustomDump` belleğin sızmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f401d-126">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f401d-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f401d-127">Requirements</span></span>  

 <span data-ttu-id="f401d-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f401d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f401d-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f401d-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f401d-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f401d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f401d-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f401d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f401d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f401d-132">See also</span></span>

- [<span data-ttu-id="f401d-133">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="f401d-133">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="f401d-134">ECustomDumpFlavor Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f401d-134">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="f401d-135">ICLRErrorReportingManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f401d-135">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)

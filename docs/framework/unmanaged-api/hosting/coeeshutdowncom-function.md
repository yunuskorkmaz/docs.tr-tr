---
title: "CoEEShutDownCOM İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ae339310c2bfd186cae798ff603d69735abeefd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="3ddfa-102">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="3ddfa-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="3ddfa-103">Ortak dil çalışma zamanı (CLR) çalışma zamanı aranabilir sarmalayıcıları (RCW) içinde tutan tüm arabirim işaretçileri yayımlamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="3ddfa-104">Bu, tüm RCW önbellekleri yayınlama etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="3ddfa-105">Bu genel işlevi de kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3ddfa-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="3ddfa-106">Bunun yerine, giriş noktası için belirli bir çalışma zamanı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ddfa-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ddfa-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3ddfa-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ddfa-108">Remarks</span></span>  
 <span data-ttu-id="3ddfa-109">`CoEEShutDownCOM` İşlevi önce tüm RCWs tüm bağlamları ve tüm önbellekleri serbest bırakır ve kurulumunda varolan herhangi bir kapatmayı aşağı bildirim kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="3ddfa-110">Hiçbir DLL'i kaldırma oluşur.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3ddfa-111">Bu işlev işlemi içinde yüklenen tüm çalışma zamanları etkiler.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="3ddfa-112">İle başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], giriş noktası üzerindeki etkiler istediğiniz belirli çalışma zamanı bu işlev çağrısı.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="3ddfa-113">Giriş noktası almak için arama [Iclrruntimeınfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) yöntemi ve "CoEEShutDownCOM" belirtin.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ddfa-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ddfa-114">Requirements</span></span>  
 <span data-ttu-id="3ddfa-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ddfa-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ddfa-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ddfa-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ddfa-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3ddfa-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ddfa-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ddfa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ddfa-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ddfa-119">See Also</span></span>  
 [<span data-ttu-id="3ddfa-120">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="3ddfa-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

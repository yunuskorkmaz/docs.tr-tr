---
title: CoEEShutDownCOM İşlevi
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d990d63a007240ab0bd0240f7b45fed52e2a2129
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212254"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="05c7e-102">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="05c7e-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="05c7e-103">Ortak dil çalışma zamanı (CLR) çalışma zamanı aranabilir sarmalayıcılarını (RCW) içinde tutan tüm arabirim işaretçilerini yayımlamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="05c7e-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="05c7e-104">Bu, tüm RCW önbellekleri bırakılıyor etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="05c7e-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="05c7e-105">Bu genel bir işlev içinde kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="05c7e-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="05c7e-106">Bunun yerine, belirli bir çalışma zamanı için giriş noktasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="05c7e-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05c7e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05c7e-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="05c7e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05c7e-108">Remarks</span></span>  
 <span data-ttu-id="05c7e-109">`CoEEShutDownCOM` İşlevi ilk tüm RCW tüm bağlamlarda ve tüm önbellekleri serbest bırakır ve sonra kurulumunda varolan herhangi bir kapatmayı bildirim kaldırır.</span><span class="sxs-lookup"><span data-stu-id="05c7e-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="05c7e-110">Hiçbir DLL'i kaldırma gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="05c7e-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="05c7e-111">Bu işlev, işlem içine yüklenmiş tüm çalışma zamanları etkiler.</span><span class="sxs-lookup"><span data-stu-id="05c7e-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="05c7e-112">İle başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], değiştirmek istediğiniz belirli çalışma zamanı üzerinde bu işlev için giriş noktası çağırın.</span><span class="sxs-lookup"><span data-stu-id="05c7e-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="05c7e-113">Giriş noktası almak için arama [Iclrruntimeınfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) yöntemi ve "CoEEShutDownCOM" belirtin.</span><span class="sxs-lookup"><span data-stu-id="05c7e-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05c7e-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05c7e-114">Requirements</span></span>  
 <span data-ttu-id="05c7e-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05c7e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05c7e-116">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="05c7e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05c7e-117">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="05c7e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05c7e-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05c7e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05c7e-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05c7e-119">See also</span></span>
- [<span data-ttu-id="05c7e-120">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="05c7e-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

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
ms.openlocfilehash: f0b30cc2c499644ffc97a734e1554e4e352b34af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431896"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="c7072-102">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="c7072-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="c7072-103">Ortak dil çalışma zamanı (CLR) çalışma zamanı aranabilir sarmalayıcıları (RCW) içinde tutan tüm arabirim işaretçileri yayımlamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="c7072-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="c7072-104">Bu, tüm RCW önbellekleri yayınlama etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="c7072-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="c7072-105">Bu genel işlevi de kullanım dışı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7072-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="c7072-106">Bunun yerine, giriş noktası için belirli bir çalışma zamanı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7072-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7072-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7072-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c7072-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7072-108">Remarks</span></span>  
 <span data-ttu-id="c7072-109">`CoEEShutDownCOM` İşlevi önce tüm RCWs tüm bağlamları ve tüm önbellekleri serbest bırakır ve kurulumunda varolan herhangi bir kapatmayı aşağı bildirim kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c7072-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="c7072-110">Hiçbir DLL'i kaldırma oluşur.</span><span class="sxs-lookup"><span data-stu-id="c7072-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c7072-111">Bu işlev işlemi içinde yüklenen tüm çalışma zamanları etkiler.</span><span class="sxs-lookup"><span data-stu-id="c7072-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="c7072-112">İle başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], giriş noktası üzerindeki etkiler istediğiniz belirli çalışma zamanı bu işlev çağrısı.</span><span class="sxs-lookup"><span data-stu-id="c7072-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="c7072-113">Giriş noktası almak için arama [Iclrruntimeınfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) yöntemi ve "CoEEShutDownCOM" belirtin.</span><span class="sxs-lookup"><span data-stu-id="c7072-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7072-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7072-114">Requirements</span></span>  
 <span data-ttu-id="c7072-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7072-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7072-116">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7072-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7072-117">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c7072-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7072-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7072-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7072-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7072-119">See Also</span></span>  
 [<span data-ttu-id="c7072-120">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c7072-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

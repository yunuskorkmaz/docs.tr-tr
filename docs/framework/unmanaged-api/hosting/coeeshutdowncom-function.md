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
ms.openlocfilehash: 164384f043a1722ace6e5c4098cb31c4327cba1e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044066"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="f5850-102">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="f5850-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="f5850-103">Ortak dil çalışma zamanını (CLR) çalışma zamanı çağrılabilir sarmalayıcılar (RCW) içinde tuttuğu tüm arabirim işaretçilerini serbest bırakmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="f5850-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="f5850-104">Bu, tüm RCW önbelleklerini serbest bırakma etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f5850-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="f5850-105">Bu genel işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f5850-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="f5850-106">Bunun yerine, belirli bir çalışma zamanı için giriş noktasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f5850-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5850-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5850-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f5850-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5850-108">Remarks</span></span>  
 <span data-ttu-id="f5850-109">`CoEEShutDownCOM` İşlevi ilk olarak tüm bağlamlardaki ve tüm önbelleklerde tüm RCWs 'ları serbest bırakır ve ardından Kurulum 'da mevcut olan tüm koparma bildirimini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f5850-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="f5850-110">DLL kaldırma gerçekleşmediğinde.</span><span class="sxs-lookup"><span data-stu-id="f5850-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f5850-111">Bu işlev, işleme yüklenen tüm çalışma zamanlarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="f5850-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="f5850-112">.NET Framework 4 ' ten başlayarak, etkilenmesini istediğiniz belirli çalışma zamanında bu işlevin giriş noktasını çağırın.</span><span class="sxs-lookup"><span data-stu-id="f5850-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="f5850-113">Giriş noktasını almak için [ICLRRuntimeInfo:: GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metodunu çağırın ve "CoEEShutDownCOM" belirtin.</span><span class="sxs-lookup"><span data-stu-id="f5850-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5850-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5850-114">Requirements</span></span>  
 <span data-ttu-id="f5850-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5850-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5850-116">**Üst bilgi** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f5850-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5850-117">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="f5850-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5850-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5850-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5850-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5850-119">See also</span></span>

- [<span data-ttu-id="f5850-120">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f5850-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

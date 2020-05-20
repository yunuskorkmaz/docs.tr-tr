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
ms.openlocfilehash: 3eb8bffee9d30a89c39a900e600ebf171456b9f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616796"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="d4fc4-102">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="d4fc4-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="d4fc4-103">Ortak dil çalışma zamanını (CLR) çalışma zamanı çağrılabilir sarmalayıcılar (RCW) içinde tuttuğu tüm arabirim işaretçilerini serbest bırakmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="d4fc4-104">Bu, tüm RCW önbelleklerini serbest bırakma etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="d4fc4-105">Bu genel işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="d4fc4-106">Bunun yerine, belirli bir çalışma zamanı için giriş noktasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4fc4-107">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d4fc4-107">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="d4fc4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4fc4-108">Remarks</span></span>  
 <span data-ttu-id="d4fc4-109">`CoEEShutDownCOM`İşlevi ilk olarak tüm bağlamlardaki ve tüm önbelleklerde tüm RCWs 'ları serbest bırakır ve ardından Kurulum 'da mevcut olan tüm koparma bildirimini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="d4fc4-110">DLL kaldırma gerçekleşmediğinde.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="d4fc4-111">Bu işlev, işleme yüklenen tüm çalışma zamanlarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="d4fc4-112">.NET Framework 4 ' ten başlayarak, etkilenmesini istediğiniz belirli çalışma zamanında bu işlevin giriş noktasını çağırın.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="d4fc4-113">Giriş noktasını almak için [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) metodunu çağırın ve "CoEEShutDownCOM" belirtin.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4fc4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4fc4-114">Requirements</span></span>  
 <span data-ttu-id="d4fc4-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4fc4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4fc4-116">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d4fc4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4fc4-117">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d4fc4-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4fc4-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4fc4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fc4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4fc4-119">See also</span></span>

- [<span data-ttu-id="d4fc4-120">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d4fc4-120">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

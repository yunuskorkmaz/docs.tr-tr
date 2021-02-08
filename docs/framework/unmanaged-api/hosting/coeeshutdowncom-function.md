---
description: 'Daha fazla bilgi edinin: CoEEShutDownCOM Işlevi'
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
ms.openlocfilehash: 4f1ac8107c9a121ebf52ef21a5f2c9006880914f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799869"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="30670-103">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="30670-103">CoEEShutDownCOM Function</span></span>

<span data-ttu-id="30670-104">Ortak dil çalışma zamanını (CLR) çalışma zamanı çağrılabilir sarmalayıcılar (RCW) içinde tuttuğu tüm arabirim işaretçilerini serbest bırakmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="30670-104">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="30670-105">Bu, tüm RCW önbelleklerini serbest bırakma etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="30670-105">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="30670-106">Bu genel işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="30670-106">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="30670-107">Bunun yerine, belirli bir çalışma zamanı için giriş noktasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="30670-107">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30670-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="30670-108">Syntax</span></span>  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="30670-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30670-109">Remarks</span></span>  

 <span data-ttu-id="30670-110">`CoEEShutDownCOM`İşlevi ilk olarak tüm bağlamlardaki ve tüm önbelleklerde tüm RCWs 'ları serbest bırakır ve ardından Kurulum 'da mevcut olan tüm koparma bildirimini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="30670-110">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="30670-111">DLL kaldırma gerçekleşmediğinde.</span><span class="sxs-lookup"><span data-stu-id="30670-111">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="30670-112">Bu işlev, işleme yüklenen tüm çalışma zamanlarını etkiler.</span><span class="sxs-lookup"><span data-stu-id="30670-112">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="30670-113">.NET Framework 4 ' ten başlayarak, etkilenmesini istediğiniz belirli çalışma zamanında bu işlevin giriş noktasını çağırın.</span><span class="sxs-lookup"><span data-stu-id="30670-113">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="30670-114">Giriş noktasını almak için [ICLRRuntimeInfo:: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) metodunu çağırın ve "CoEEShutDownCOM" belirtin.</span><span class="sxs-lookup"><span data-stu-id="30670-114">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30670-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30670-115">Requirements</span></span>  

 <span data-ttu-id="30670-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30670-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30670-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="30670-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30670-118">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="30670-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30670-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30670-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30670-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30670-120">See also</span></span>

- [<span data-ttu-id="30670-121">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="30670-121">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

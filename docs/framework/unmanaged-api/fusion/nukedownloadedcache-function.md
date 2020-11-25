---
title: NukeDownloadedCache İşlevi
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
ms.openlocfilehash: 5ae0a887d666a150b717d495848c8a411d030a09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728582"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="81ede-102">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="81ede-102">NukeDownloadedCache Function</span></span>

<span data-ttu-id="81ede-103">Ortak dil çalışma zamanı (CLR) indirme önbelleğini siler.</span><span class="sxs-lookup"><span data-stu-id="81ede-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81ede-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="81ede-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="81ede-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="81ede-105">Return Value</span></span>  

 <span data-ttu-id="81ede-106">Bu yöntem, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="81ede-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81ede-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81ede-107">Remarks</span></span>  

 <span data-ttu-id="81ede-108">CLR indirme önbelleği, bir URL 'den indirilen tanımlayıcı adlı derlemelerin olası yeniden kullanım için depolandığı alandır.</span><span class="sxs-lookup"><span data-stu-id="81ede-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81ede-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="81ede-109">Requirements</span></span>  

 <span data-ttu-id="81ede-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81ede-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81ede-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="81ede-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="81ede-112">**Kitaplık:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="81ede-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="81ede-113">Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="81ede-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="81ede-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81ede-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ede-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81ede-115">See also</span></span>

- [<span data-ttu-id="81ede-116">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="81ede-116">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="81ede-117">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="81ede-117">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="81ede-118">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="81ede-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)

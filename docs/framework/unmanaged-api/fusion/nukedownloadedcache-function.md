---
description: 'Daha fazla bilgi edinin: NukeDownloadedCache Işlevi'
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
ms.openlocfilehash: 2239473b8e6e43a539b0507c8255d40f87e72043
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800038"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="682bf-103">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="682bf-103">NukeDownloadedCache Function</span></span>

<span data-ttu-id="682bf-104">Ortak dil çalışma zamanı (CLR) indirme önbelleğini siler.</span><span class="sxs-lookup"><span data-stu-id="682bf-104">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="682bf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="682bf-105">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="682bf-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="682bf-106">Return Value</span></span>  

 <span data-ttu-id="682bf-107">Bu yöntem, WinError. h içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="682bf-107">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="682bf-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="682bf-108">Remarks</span></span>  

 <span data-ttu-id="682bf-109">CLR indirme önbelleği, bir URL 'den indirilen tanımlayıcı adlı derlemelerin olası yeniden kullanım için depolandığı alandır.</span><span class="sxs-lookup"><span data-stu-id="682bf-109">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="682bf-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="682bf-110">Requirements</span></span>  

 <span data-ttu-id="682bf-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="682bf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="682bf-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="682bf-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="682bf-113">**Kitaplık:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="682bf-113">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="682bf-114">Doğru .NET Framework sürümünü hedefliyorsanız emin olmak için Mscorwks.dll yerine Fusion.dll kullanın.</span><span class="sxs-lookup"><span data-stu-id="682bf-114">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="682bf-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="682bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="682bf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="682bf-116">See also</span></span>

- [<span data-ttu-id="682bf-117">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="682bf-117">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="682bf-118">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="682bf-118">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="682bf-119">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="682bf-119">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)

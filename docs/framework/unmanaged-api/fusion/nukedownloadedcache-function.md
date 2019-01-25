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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80891da7d61aa5114d5cc4d8aff4c7ce82020237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720099"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="32aab-102">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="32aab-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="32aab-103">Ortak dil çalışma zamanı (CLR) indirme önbelleğini siler.</span><span class="sxs-lookup"><span data-stu-id="32aab-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32aab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32aab-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="32aab-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32aab-105">Return Value</span></span>  
 <span data-ttu-id="32aab-106">Bu yöntem, Wınerror içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="32aab-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32aab-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32aab-107">Remarks</span></span>  
 <span data-ttu-id="32aab-108">CLR indirme önbelleğini URL'den indirilen tanımlayıcı adlı derlemeler için olası yeniden depolandığı alanıdır.</span><span class="sxs-lookup"><span data-stu-id="32aab-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32aab-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32aab-109">Requirements</span></span>  
 <span data-ttu-id="32aab-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32aab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32aab-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="32aab-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="32aab-112">**Kitaplığı:** Fusion.dll ve kullanımda olan mscorwks.dll'ye.</span><span class="sxs-lookup"><span data-stu-id="32aab-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="32aab-113">Fusion.dll yerine Mscorwks.dll doğru .NET Framework sürümünü hedefleyen emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="32aab-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="32aab-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32aab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32aab-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32aab-115">See also</span></span>
- [<span data-ttu-id="32aab-116">CreateHistoryReader İşlevi</span><span class="sxs-lookup"><span data-stu-id="32aab-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="32aab-117">GetHistoryFileDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="32aab-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [<span data-ttu-id="32aab-118">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="32aab-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

---
title: "NukeDownloadedCache İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: NukeDownloadedCache
helpviewer_keywords: NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ff24cf46ab24fe94ab19cee04d9e32ed1a34b53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="70d5e-102">NukeDownloadedCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="70d5e-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="70d5e-103">Ortak dil çalışma zamanı (CLR) indirme önbelleğini siler.</span><span class="sxs-lookup"><span data-stu-id="70d5e-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70d5e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70d5e-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="70d5e-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="70d5e-105">Return Value</span></span>  
 <span data-ttu-id="70d5e-106">Bu yöntem, Winerror.h'de içinde tanımlanan standart COM hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="70d5e-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70d5e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70d5e-107">Remarks</span></span>  
 <span data-ttu-id="70d5e-108">CLR yükleme önbelleği bir URL'den indirilen tanımlayıcı adlı derlemeler için olası yeniden depolandığı alanıdır.</span><span class="sxs-lookup"><span data-stu-id="70d5e-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70d5e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70d5e-109">Requirements</span></span>  
 <span data-ttu-id="70d5e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70d5e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70d5e-111">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="70d5e-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="70d5e-112">**Kitaplığı:** Fusion.dll ve Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="70d5e-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="70d5e-113">Fusion.dll Mscorwks.dll yerine .NET Framework'ün doğru sürümünü hedef emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="70d5e-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="70d5e-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70d5e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d5e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70d5e-115">See Also</span></span>  
 [<span data-ttu-id="70d5e-116">CreateHistoryReader işlevi</span><span class="sxs-lookup"><span data-stu-id="70d5e-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="70d5e-117">GetHistoryFileDirectory işlevi</span><span class="sxs-lookup"><span data-stu-id="70d5e-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="70d5e-118">Fusion genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="70d5e-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)

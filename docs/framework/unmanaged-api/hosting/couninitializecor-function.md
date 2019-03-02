---
title: CoUninitializeCor İşlevi
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dca4fd4a4d20627bef8f7fedd5a801ba07e8e19b
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212085"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="4fccc-102">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="4fccc-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="4fccc-103">`CoUninitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="4fccc-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fccc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4fccc-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="4fccc-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fccc-105">Remarks</span></span>  
 <span data-ttu-id="4fccc-106">Ortak dil çalışma zamanı bir işlemden olamaz.</span><span class="sxs-lookup"><span data-stu-id="4fccc-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="4fccc-107">Çalışma zamanı çalışan bir işlemden tamamen kaldırmak için bu işlemi kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4fccc-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fccc-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fccc-108">See also</span></span>
- [<span data-ttu-id="4fccc-109">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="4fccc-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

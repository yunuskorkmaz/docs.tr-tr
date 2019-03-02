---
title: CoUninitializeEE İşlevi
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c4e22c2e80af37177294d86c2e5775a5c296fe7
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211864"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="fdaaa-102">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="fdaaa-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="fdaaa-103">`CoUninitializeEE` artık kullanılmıyor ve hiçbir işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="fdaaa-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdaaa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdaaa-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="fdaaa-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdaaa-105">Remarks</span></span>  
 <span data-ttu-id="fdaaa-106">Ortak dil çalışma zamanı yürütme altyapısının bir işlemden olamaz.</span><span class="sxs-lookup"><span data-stu-id="fdaaa-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="fdaaa-107">Yürütme altyapısı çağrıyı kapatmaya [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="fdaaa-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdaaa-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdaaa-108">See also</span></span>
- [<span data-ttu-id="fdaaa-109">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="fdaaa-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="fdaaa-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fdaaa-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

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
ms.openlocfilehash: 7b3712b4cb66facc105a03d7bfad235f09339056
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193011"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="6de7e-102">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="6de7e-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="6de7e-103">`CoUninitializeEE` artık kullanılmıyor ve hiçbir işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="6de7e-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6de7e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6de7e-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="6de7e-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6de7e-105">Remarks</span></span>  
 <span data-ttu-id="6de7e-106">Ortak dil çalışma zamanı yürütme altyapısının bir işlemden olamaz.</span><span class="sxs-lookup"><span data-stu-id="6de7e-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="6de7e-107">Yürütme altyapısı çağrıyı kapatmaya [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="6de7e-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6de7e-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6de7e-108">See also</span></span>

- [<span data-ttu-id="6de7e-109">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="6de7e-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="6de7e-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6de7e-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

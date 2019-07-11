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
ms.openlocfilehash: d05bc472711838236ed18b00ce808d022d9581dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758208"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="1ac79-102">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="1ac79-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="1ac79-103">`CoUninitializeEE` artık kullanılmıyor ve hiçbir işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ac79-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ac79-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="1ac79-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1ac79-105">Remarks</span></span>  
 <span data-ttu-id="1ac79-106">Ortak dil çalışma zamanı yürütme altyapısının bir işlemden olamaz.</span><span class="sxs-lookup"><span data-stu-id="1ac79-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="1ac79-107">Yürütme altyapısı çağrıyı kapatmaya [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="1ac79-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac79-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ac79-108">See also</span></span>

- [<span data-ttu-id="1ac79-109">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="1ac79-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="1ac79-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1ac79-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

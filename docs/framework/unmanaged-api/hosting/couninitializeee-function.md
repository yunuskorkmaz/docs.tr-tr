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
ms.openlocfilehash: 3531cfc0815c3f8a9479e35b2df60b2825801b39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136857"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="cf8da-102">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="cf8da-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="cf8da-103">`CoUninitializeEE` artık kullanılmıyor ve hiçbir işlev sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="cf8da-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf8da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf8da-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf8da-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf8da-105">Remarks</span></span>  
 <span data-ttu-id="cf8da-106">Ortak dil çalışma zamanı yürütme altyapısı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="cf8da-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="cf8da-107">Yürütme altyapısını kapatmak için, [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)çağrısını çağırın.</span><span class="sxs-lookup"><span data-stu-id="cf8da-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8da-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf8da-108">See also</span></span>

- [<span data-ttu-id="cf8da-109">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="cf8da-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="cf8da-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cf8da-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

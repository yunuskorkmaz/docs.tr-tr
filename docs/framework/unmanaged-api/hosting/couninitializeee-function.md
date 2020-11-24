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
ms.openlocfilehash: e6616392eaa23f8ba40247c5aabd12e4d530cea1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687853"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="16368-102">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="16368-102">CoUninitializeEE Function</span></span>

<span data-ttu-id="16368-103">`CoUninitializeEE` artık kullanılmıyor ve hiçbir işlev sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="16368-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16368-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="16368-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="16368-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16368-105">Remarks</span></span>  

 <span data-ttu-id="16368-106">Ortak dil çalışma zamanı yürütme altyapısı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="16368-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="16368-107">Yürütme altyapısını kapatmak için, [CorExitProcess](corexitprocess-function.md)çağrısını çağırın.</span><span class="sxs-lookup"><span data-stu-id="16368-107">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16368-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16368-108">See also</span></span>

- [<span data-ttu-id="16368-109">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="16368-109">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="16368-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="16368-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

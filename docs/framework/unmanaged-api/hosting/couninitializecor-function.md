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
ms.openlocfilehash: 7d39c6fda6f159bfc937f62dc45d0d7ce37657f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687887"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="11ec6-102">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="11ec6-102">CoUninitializeCor Function</span></span>

<span data-ttu-id="11ec6-103">`CoUninitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="11ec6-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11ec6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="11ec6-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="11ec6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11ec6-105">Remarks</span></span>  

 <span data-ttu-id="11ec6-106">Ortak dil çalışma zamanı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="11ec6-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="11ec6-107">Çalışma zamanını çalışan bir işlemden tamamen kaldırmak için bu işlemi kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="11ec6-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ec6-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11ec6-108">See also</span></span>

- [<span data-ttu-id="11ec6-109">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="11ec6-109">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

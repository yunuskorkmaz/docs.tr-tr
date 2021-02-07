---
description: 'Daha fazla bilgi edinin: Counınitializecor Işlevi'
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
ms.openlocfilehash: 1aa3482b6891779b4c85c29079ccd26d7170934e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746210"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="44884-103">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="44884-103">CoUninitializeCor Function</span></span>

<span data-ttu-id="44884-104">`CoUninitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="44884-104">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44884-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="44884-105">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="44884-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44884-106">Remarks</span></span>  

 <span data-ttu-id="44884-107">Ortak dil çalışma zamanı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="44884-107">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="44884-108">Çalışma zamanını çalışan bir işlemden tamamen kaldırmak için bu işlemi kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="44884-108">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44884-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44884-109">See also</span></span>

- [<span data-ttu-id="44884-110">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="44884-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

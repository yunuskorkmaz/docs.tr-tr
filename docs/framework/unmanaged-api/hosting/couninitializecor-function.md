---
title: "CoUninitializeCor İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoUninitializeCor
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoUninitializeCor
helpviewer_keywords: CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 57740ed8f20891b240bca5e9e19591484022b8ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="couninitializecor-function"></a><span data-ttu-id="630cf-102">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="630cf-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="630cf-103">`CoUninitializeCor`Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="630cf-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="630cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="630cf-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="630cf-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="630cf-105">Remarks</span></span>  
 <span data-ttu-id="630cf-106">Ortak dil çalışma zamanı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="630cf-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="630cf-107">Çalışma zamanı çalışan işleminden tamamen kaldırmak için bu işlemi kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="630cf-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630cf-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="630cf-108">See Also</span></span>  
 [<span data-ttu-id="630cf-109">Meta veri genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="630cf-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

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
ms.openlocfilehash: 0845c4d493cb3c750931a0ae2ad92b628a255c0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985757"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="438ca-102">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="438ca-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="438ca-103">`CoUninitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="438ca-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="438ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="438ca-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="438ca-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="438ca-105">Remarks</span></span>  
 <span data-ttu-id="438ca-106">Ortak dil çalışma zamanı bir işlemden olamaz.</span><span class="sxs-lookup"><span data-stu-id="438ca-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="438ca-107">Çalışma zamanı çalışan bir işlemden tamamen kaldırmak için bu işlemi kapatmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="438ca-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438ca-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="438ca-108">See also</span></span>

- [<span data-ttu-id="438ca-109">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="438ca-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)

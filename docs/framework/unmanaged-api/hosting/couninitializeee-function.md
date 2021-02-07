---
description: 'Daha fazla bilgi edinin: Counınitialeee Işlevi'
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
ms.openlocfilehash: e356135ea027bd52520eff9084ad2f7f09e1fe0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746171"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="fcc92-103">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="fcc92-103">CoUninitializeEE Function</span></span>

<span data-ttu-id="fcc92-104">`CoUninitializeEE` artık kullanılmıyor ve hiçbir işlev sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="fcc92-104">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc92-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fcc92-105">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="fcc92-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fcc92-106">Remarks</span></span>  

 <span data-ttu-id="fcc92-107">Ortak dil çalışma zamanı yürütme altyapısı bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="fcc92-107">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="fcc92-108">Yürütme altyapısını kapatmak için, [CorExitProcess](corexitprocess-function.md)çağrısını çağırın.</span><span class="sxs-lookup"><span data-stu-id="fcc92-108">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc92-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fcc92-109">See also</span></span>

- [<span data-ttu-id="fcc92-110">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="fcc92-110">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="fcc92-111">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="fcc92-111">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

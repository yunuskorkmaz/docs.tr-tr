---
description: 'Daha fazla bilgi edinin: CoInitializeCor Işlevi'
title: CoInitializeCor İşlevi
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: e1db9914cce8a92cecf78123a2e247d75ec74acf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799856"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="ff4fa-103">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="ff4fa-103">CoInitializeCor Function</span></span>

<span data-ttu-id="ff4fa-104">`CoInitializeCor` artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="ff4fa-104">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4fa-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ff4fa-105">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="ff4fa-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff4fa-106">Remarks</span></span>  

 <span data-ttu-id="ff4fa-107">Ortak dil çalışma zamanını başlatmak için [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="ff4fa-107">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff4fa-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff4fa-108">Requirements</span></span>  

 <span data-ttu-id="ff4fa-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ff4fa-109">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4fa-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff4fa-110">See also</span></span>

- [<span data-ttu-id="ff4fa-111">Meta Veri Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ff4fa-111">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)

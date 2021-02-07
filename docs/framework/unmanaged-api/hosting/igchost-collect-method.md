---
description: 'Daha fazla bilgi edinin: IGCHost:: Collect yöntemi'
title: IGCHost::Collect Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: b4c249e07709dc443ae7dd6c6a5bfd206b7f1caa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709704"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="7fdc8-103">IGCHost::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7fdc8-103">IGCHost::Collect Method</span></span>

<span data-ttu-id="7fdc8-104">Geçerli çöp toplamanın durumundan bağımsız olarak, belirli bir oluşturma için bir koleksiyonu meydana gelecek şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="7fdc8-104">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fdc8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7fdc8-105">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fdc8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7fdc8-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="7fdc8-107">'ndaki Çöp toplamanın gerçekleştirileceği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="7fdc8-107">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="7fdc8-108">-1 değeri, tüm nesiller 'in çöp toplama işlemini üstlendiridiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fdc8-108">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fdc8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7fdc8-109">Requirements</span></span>  

 <span data-ttu-id="7fdc8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fdc8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fdc8-111">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="7fdc8-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="7fdc8-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="7fdc8-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fdc8-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fdc8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fdc8-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fdc8-114">See also</span></span>

- [<span data-ttu-id="7fdc8-115">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7fdc8-115">IGCHost Interface</span></span>](igchost-interface.md)

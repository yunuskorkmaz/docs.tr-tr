---
description: ': ICorConfiguration:: SetDebuggerThreadControl yöntemi hakkında daha fazla bilgi edinin'
title: ICorConfiguration::SetDebuggerThreadControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
ms.openlocfilehash: 9bf024f3feb6df44a94f8a5f1a626bb6e0c91d31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636669"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="e80c4-103">ICorConfiguration::SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e80c4-103">ICorConfiguration::SetDebuggerThreadControl Method</span></span>

<span data-ttu-id="e80c4-104">Hata ayıklama hizmetlerinin, ortak dil çalışma zamanı (CLR) iş parçacıklarının engellediği ve hata ayıklama için engellemesi kaldırıldığından, geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e80c4-104">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e80c4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e80c4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e80c4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e80c4-106">Parameters</span></span>  

 `pDebuggerThreadControl`  
 <span data-ttu-id="e80c4-107">'ndaki Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesini ve engellemesini kaldırma hakkında bilgi veren bir [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e80c4-107">[in] A pointer to an [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e80c4-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e80c4-108">Requirements</span></span>  

 <span data-ttu-id="e80c4-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e80c4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e80c4-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e80c4-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e80c4-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e80c4-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e80c4-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e80c4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80c4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e80c4-113">See also</span></span>

- [<span data-ttu-id="e80c4-114">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e80c4-114">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)

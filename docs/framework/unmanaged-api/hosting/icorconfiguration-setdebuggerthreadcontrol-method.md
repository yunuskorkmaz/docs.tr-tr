---
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
ms.openlocfilehash: 05df50d80c6b8962b3bdfe2708d5f9d30c58aaea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723928"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="05b7b-102">ICorConfiguration::SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05b7b-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>

<span data-ttu-id="05b7b-103">Hata ayıklama hizmetlerinin, ortak dil çalışma zamanı (CLR) iş parçacıklarının engellediği ve hata ayıklama için engellemesi kaldırıldığından, geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="05b7b-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b7b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="05b7b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05b7b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05b7b-105">Parameters</span></span>  

 `pDebuggerThreadControl`  
 <span data-ttu-id="05b7b-106">'ndaki Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesini ve engellemesini kaldırma hakkında bilgi veren bir [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05b7b-106">[in] A pointer to an [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05b7b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05b7b-107">Requirements</span></span>  

 <span data-ttu-id="05b7b-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05b7b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05b7b-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="05b7b-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05b7b-110">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="05b7b-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05b7b-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05b7b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b7b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05b7b-112">See also</span></span>

- [<span data-ttu-id="05b7b-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05b7b-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)

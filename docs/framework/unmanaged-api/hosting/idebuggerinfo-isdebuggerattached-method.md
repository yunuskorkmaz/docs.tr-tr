---
title: IDebuggerInfo::IsDebuggerAttached Yöntemi
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
ms.openlocfilehash: 95b7a2f6d35104c3353853549dacc783355feb5b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805328"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="ef7d6-102">IDebuggerInfo::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef7d6-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="ef7d6-103">Yönetilen bir hata ayıklayıcının bu işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ef7d6-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef7d6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ef7d6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef7d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef7d6-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="ef7d6-106">dışı `true`Yönetilen bir hata ayıklayıcı işleme eklenmişse bir değere yönelik işaretçi; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="ef7d6-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef7d6-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef7d6-107">Requirements</span></span>  
 <span data-ttu-id="ef7d6-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef7d6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef7d6-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ef7d6-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef7d6-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ef7d6-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef7d6-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef7d6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef7d6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef7d6-112">See also</span></span>

- [<span data-ttu-id="ef7d6-113">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef7d6-113">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)

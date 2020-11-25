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
ms.openlocfilehash: 28b0c5ad5ed8b706974399dcd5468e9810b9fd57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721705"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="b79f4-102">IDebuggerInfo::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b79f4-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>

<span data-ttu-id="b79f4-103">Yönetilen bir hata ayıklayıcının bu işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b79f4-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b79f4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b79f4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b79f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b79f4-105">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="b79f4-106">dışı `true` Yönetilen bir hata ayıklayıcı işleme eklenmişse bir değere yönelik işaretçi; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="b79f4-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b79f4-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b79f4-107">Requirements</span></span>  

 <span data-ttu-id="b79f4-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b79f4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b79f4-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b79f4-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b79f4-110">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b79f4-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b79f4-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b79f4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79f4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b79f4-112">See also</span></span>

- [<span data-ttu-id="b79f4-113">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b79f4-113">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)

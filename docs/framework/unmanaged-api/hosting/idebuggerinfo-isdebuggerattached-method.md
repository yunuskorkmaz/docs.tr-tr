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
ms.openlocfilehash: cbd6fa5f7935a57799d695c3ebb617d856e6dbd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133170"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="d4f46-102">IDebuggerInfo::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4f46-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="d4f46-103">Yönetilen bir hata ayıklayıcının bu işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d4f46-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4f46-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4f46-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4f46-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="d4f46-106">dışı Yönetilen bir hata ayıklayıcı işleme eklenmişse `true` bir değere yönelik işaretçi. Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="d4f46-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f46-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4f46-107">Requirements</span></span>  
 <span data-ttu-id="d4f46-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4f46-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4f46-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4f46-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4f46-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d4f46-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4f46-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f46-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f46-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4f46-112">See also</span></span>

- [<span data-ttu-id="d4f46-113">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4f46-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)

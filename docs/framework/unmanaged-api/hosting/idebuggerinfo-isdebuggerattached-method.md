---
description: 'Şu konuda daha fazla bilgi edinin: IDebuggerInfo:: ısdebuggerekli yöntemi'
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
ms.openlocfilehash: a17a7f5f1cef1d0c7025f4051e59767ce09ec421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709817"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="f0fe1-103">IDebuggerInfo::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0fe1-103">IDebuggerInfo::IsDebuggerAttached Method</span></span>

<span data-ttu-id="f0fe1-104">Yönetilen bir hata ayıklayıcının bu işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="f0fe1-104">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0fe1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0fe1-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0fe1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0fe1-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="f0fe1-107">dışı `true` Yönetilen bir hata ayıklayıcı işleme eklenmişse bir değere yönelik işaretçi; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="f0fe1-107">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0fe1-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0fe1-108">Requirements</span></span>  

 <span data-ttu-id="f0fe1-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0fe1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0fe1-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f0fe1-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0fe1-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f0fe1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0fe1-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0fe1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0fe1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0fe1-113">See also</span></span>

- [<span data-ttu-id="f0fe1-114">IDebuggerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0fe1-114">IDebuggerInfo Interface</span></span>](idebuggerinfo-interface.md)

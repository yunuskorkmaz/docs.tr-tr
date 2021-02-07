---
description: ': IObjectHandle:: Unwrap yöntemi hakkında daha fazla bilgi edinin'
title: IObjectHandle::Unwrap Yöntemi
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
ms.openlocfilehash: 3f791eaf52abd045d495fe15e868423e464fd27e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728333"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="d5075-103">IObjectHandle::Unwrap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5075-103">IObjectHandle::Unwrap Method</span></span>

<span data-ttu-id="d5075-104">Bir değere göre sıralama nesnesinin yöneltme şeklini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="d5075-104">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5075-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5075-105">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5075-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5075-106">Parameters</span></span>  

 `ppv`  
 <span data-ttu-id="d5075-107">dışı Sarmalanmamış nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d5075-107">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5075-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5075-108">Requirements</span></span>  

 <span data-ttu-id="d5075-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5075-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5075-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d5075-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5075-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d5075-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5075-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5075-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

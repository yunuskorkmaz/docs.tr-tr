---
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
ms.openlocfilehash: 0ff088731514b2da0d8b1fa51ef48d8b71d16528
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842237"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="e372d-102">IObjectHandle::Unwrap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e372d-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="e372d-103">Bir değere göre sıralama nesnesinin yöneltme şeklini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e372d-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e372d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e372d-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e372d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e372d-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="e372d-106">dışı Sarmalanmamış nesne için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e372d-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e372d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e372d-107">Requirements</span></span>  
 <span data-ttu-id="e372d-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e372d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e372d-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e372d-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e372d-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e372d-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e372d-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e372d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  

---
title: IAssemblyEnum::GetNextAssembly Metodu
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
ms.openlocfilehash: ade404557d65fa073b6a0e66fe8234b41223ecde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134432"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="938cf-102">IAssemblyEnum::GetNextAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="938cf-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="938cf-103">Bu [IAssemblyEnum](iassemblyenum-interface.md) nesnesinde bulunan sonraki [IAssemblyName](iassemblyname-interface.md) öğesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="938cf-103">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="938cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="938cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="938cf-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="938cf-106">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="938cf-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="938cf-107">`pvReserved`, null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="938cf-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="938cf-108">dışı Döndürülen `IAssemblyName` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="938cf-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="938cf-109">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="938cf-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="938cf-110">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="938cf-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="938cf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="938cf-111">Requirements</span></span>  
 <span data-ttu-id="938cf-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="938cf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938cf-113">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="938cf-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="938cf-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="938cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938cf-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="938cf-115">See also</span></span>

- [<span data-ttu-id="938cf-116">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="938cf-116">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="938cf-117">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="938cf-117">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)

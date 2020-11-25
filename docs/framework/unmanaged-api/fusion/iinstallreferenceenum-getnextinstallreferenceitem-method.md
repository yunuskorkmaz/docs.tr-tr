---
title: IInstallReferenceEnum::GetNextInstallReferenceItem Metodu
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
ms.openlocfilehash: e093de7d2c2388274cbe9ebbe46084ee6ae3ff8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721107"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="21180-102">IInstallReferenceEnum::GetNextInstallReferenceItem Metodu</span><span class="sxs-lookup"><span data-stu-id="21180-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>

<span data-ttu-id="21180-103">Bu [IInstallReferenceEnum](iinstallreferenceenum-interface.md) nesnesinde bulunan Next [IInstallReferenceItem](iinstallreferenceitem-interface.md) nesnesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="21180-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21180-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="21180-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21180-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21180-105">Parameters</span></span>  

 `ppRefItem`  
 <span data-ttu-id="21180-106">dışı Döndürülen `IInstallReferenceItem` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21180-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="21180-107">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="21180-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="21180-108">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21180-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="21180-109">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="21180-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="21180-110">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="21180-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21180-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21180-111">Requirements</span></span>  

 <span data-ttu-id="21180-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21180-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21180-113">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="21180-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="21180-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21180-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21180-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21180-115">See also</span></span>

- [<span data-ttu-id="21180-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21180-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="21180-117">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21180-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)

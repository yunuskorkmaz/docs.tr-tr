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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20e2bff4257df64f761fd8fff880643d4e786748
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796449"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="cfba6-102">IInstallReferenceEnum::GetNextInstallReferenceItem Metodu</span><span class="sxs-lookup"><span data-stu-id="cfba6-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="cfba6-103">Bu [IInstallReferenceEnum](iinstallreferenceenum-interface.md) nesnesinde bulunan Next [IInstallReferenceItem](iinstallreferenceitem-interface.md) nesnesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="cfba6-103">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfba6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfba6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfba6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfba6-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="cfba6-106">dışı Döndürülen `IInstallReferenceItem` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfba6-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cfba6-107">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cfba6-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cfba6-108">`dwFlags`0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cfba6-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="cfba6-109">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="cfba6-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="cfba6-110">`pvReserved`null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cfba6-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfba6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfba6-111">Requirements</span></span>  
 <span data-ttu-id="cfba6-112">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfba6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfba6-113">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="cfba6-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cfba6-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfba6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfba6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfba6-115">See also</span></span>

- [<span data-ttu-id="cfba6-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfba6-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="cfba6-117">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfba6-117">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)

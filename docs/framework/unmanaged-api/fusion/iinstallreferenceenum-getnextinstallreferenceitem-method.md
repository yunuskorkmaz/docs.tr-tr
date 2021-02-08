---
description: 'Şu konuda daha fazla bilgi edinin: IInstallReferenceEnum:: GetNextInstallReferenceItem yöntemi'
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
ms.openlocfilehash: d410407fe16a46b45786ff74f694aaa8931be542
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800129"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="fe655-103">IInstallReferenceEnum::GetNextInstallReferenceItem Metodu</span><span class="sxs-lookup"><span data-stu-id="fe655-103">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>

<span data-ttu-id="fe655-104">Bu [IInstallReferenceEnum](iinstallreferenceenum-interface.md) nesnesinde bulunan Next [IInstallReferenceItem](iinstallreferenceitem-interface.md) nesnesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="fe655-104">Gets a pointer to the next [IInstallReferenceItem](iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe655-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe655-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe655-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe655-106">Parameters</span></span>  

 `ppRefItem`  
 <span data-ttu-id="fe655-107">dışı Döndürülen `IInstallReferenceItem` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fe655-107">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fe655-108">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe655-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="fe655-109">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe655-109">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="fe655-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe655-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="fe655-111">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe655-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe655-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe655-112">Requirements</span></span>  

 <span data-ttu-id="fe655-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe655-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe655-114">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="fe655-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fe655-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe655-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe655-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe655-116">See also</span></span>

- [<span data-ttu-id="fe655-117">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe655-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="fe655-118">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe655-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)

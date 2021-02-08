---
description: 'Şu konuda daha fazla bilgi edinin: IInstallReferenceItem:: GetReference Yöntemi'
title: IInstallReferenceItem::GetReference Yöntemi
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
ms.openlocfilehash: 88f5ca21b6f3494031e1cd232f71253e39d9e648
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800126"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="167e4-103">IInstallReferenceItem::GetReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="167e4-103">IInstallReferenceItem::GetReference Method</span></span>

<span data-ttu-id="167e4-104">Bu [IInstallReferenceItem](iinstallreferenceitem-interface.md) nesnesi tarafından temsil edilen [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) yapısına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="167e4-104">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="167e4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="167e4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="167e4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="167e4-106">Parameters</span></span>  

 `ppRefData`  
 <span data-ttu-id="167e4-107">dışı Döndürülen `FUSION_INSTALL_REFERENCE` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="167e4-107">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="167e4-108">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="167e4-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="167e4-109">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="167e4-109">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="167e4-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="167e4-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="167e4-111">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="167e4-111">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="167e4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="167e4-112">Requirements</span></span>  

 <span data-ttu-id="167e4-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="167e4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="167e4-114">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="167e4-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="167e4-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="167e4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167e4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="167e4-116">See also</span></span>

- [<span data-ttu-id="167e4-117">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="167e4-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="167e4-118">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="167e4-118">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)

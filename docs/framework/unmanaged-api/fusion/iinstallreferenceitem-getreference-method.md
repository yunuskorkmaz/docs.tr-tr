---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9395fcc6d896114c25770edbc17761323285099f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796400"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="ad0b2-102">IInstallReferenceItem::GetReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad0b2-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="ad0b2-103">Bu [IInstallReferenceItem](iinstallreferenceitem-interface.md) nesnesinin temsil ettiği [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) yapısına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ad0b2-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad0b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad0b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad0b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad0b2-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="ad0b2-106">dışı Döndürülen `FUSION_INSTALL_REFERENCE` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ad0b2-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ad0b2-107">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ad0b2-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ad0b2-108">`dwFlags`0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad0b2-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="ad0b2-109">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ad0b2-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="ad0b2-110">`pvReserved`null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad0b2-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad0b2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad0b2-111">Requirements</span></span>  
 <span data-ttu-id="ad0b2-112">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad0b2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad0b2-113">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="ad0b2-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ad0b2-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad0b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0b2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad0b2-115">See also</span></span>

- [<span data-ttu-id="ad0b2-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad0b2-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="ad0b2-117">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="ad0b2-117">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)

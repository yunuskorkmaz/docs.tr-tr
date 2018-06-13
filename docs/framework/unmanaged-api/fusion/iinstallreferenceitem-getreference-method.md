---
title: IInstallReferenceItem::GetReference Metodu
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
ms.openlocfilehash: a6c64b98f3b5ab0445b076b0d3bacfaa398e26f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429774"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="d0699-102">IInstallReferenceItem::GetReference Metodu</span><span class="sxs-lookup"><span data-stu-id="d0699-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="d0699-103">Bir işaretçi alır [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) bu tarafından temsil edilen yapısı [Iınstallreferenceıtem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d0699-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0699-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0699-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d0699-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0699-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="d0699-106">[out] Döndürülen `FUSION_INSTALL_REFERENCE` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d0699-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="d0699-107">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d0699-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d0699-108">`dwFlags` 0 (sıfır) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0699-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d0699-109">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="d0699-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d0699-110">`pvReserved` bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0699-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0699-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0699-111">Requirements</span></span>  
 <span data-ttu-id="d0699-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0699-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0699-113">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d0699-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d0699-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0699-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0699-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0699-115">See Also</span></span>  
 [<span data-ttu-id="d0699-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0699-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="d0699-117">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="d0699-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)

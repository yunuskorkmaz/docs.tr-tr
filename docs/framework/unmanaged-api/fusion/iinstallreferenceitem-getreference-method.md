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
ms.openlocfilehash: 85c3fb601cd013eff889e794e71512533f1b12ec
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484686"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="f722c-102">IInstallReferenceItem::GetReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f722c-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="f722c-103">Bir işaretçi alır [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) bu tarafından temsil edilen yapısı [Iınstallreferenceıtem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="f722c-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f722c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f722c-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f722c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f722c-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="f722c-106">[out] Döndürülen `FUSION_INSTALL_REFERENCE` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f722c-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f722c-107">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="f722c-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f722c-108">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f722c-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f722c-109">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="f722c-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f722c-110">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f722c-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f722c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f722c-111">Requirements</span></span>  
 <span data-ttu-id="f722c-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f722c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f722c-113">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f722c-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f722c-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f722c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f722c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f722c-115">See also</span></span>
- [<span data-ttu-id="f722c-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f722c-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="f722c-117">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="f722c-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)

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
ms.openlocfilehash: c768091f84157ea651c018fa89cdeafcce6c02df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537679"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="abdb0-102">IInstallReferenceItem::GetReference Metodu</span><span class="sxs-lookup"><span data-stu-id="abdb0-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="abdb0-103">Bir işaretçi alır [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) bu tarafından temsil edilen yapısı [Iınstallreferenceıtem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="abdb0-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abdb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abdb0-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abdb0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abdb0-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="abdb0-106">[out] Döndürülen `FUSION_INSTALL_REFERENCE` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="abdb0-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="abdb0-107">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="abdb0-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="abdb0-108">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abdb0-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="abdb0-109">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="abdb0-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="abdb0-110">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="abdb0-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abdb0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abdb0-111">Requirements</span></span>  
 <span data-ttu-id="abdb0-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abdb0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abdb0-113">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="abdb0-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="abdb0-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abdb0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abdb0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abdb0-115">See also</span></span>
- [<span data-ttu-id="abdb0-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abdb0-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="abdb0-117">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="abdb0-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)

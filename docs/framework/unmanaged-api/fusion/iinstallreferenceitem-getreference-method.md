---
title: IInstallReferenceItem::GetReference Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceItem.GetReference
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8686e27e63d7363e61bf4c8f1898b71d21fda52b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="4cc15-102">IInstallReferenceItem::GetReference Metodu</span><span class="sxs-lookup"><span data-stu-id="4cc15-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="4cc15-103">Bir işaretçi alır [fusıon_ınstall_reference](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) bu tarafından temsil edilen yapısı [Iınstallreferenceıtem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4cc15-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc15-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cc15-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cc15-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cc15-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="4cc15-106">[out] Döndürülen `FUSION_INSTALL_REFERENCE` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4cc15-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4cc15-107">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="4cc15-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4cc15-108">`dwFlags`0 (sıfır) olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4cc15-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="4cc15-109">[in] Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="4cc15-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="4cc15-110">`pvReserved`bir null başvuru olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4cc15-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cc15-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4cc15-111">Requirements</span></span>  
 <span data-ttu-id="4cc15-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cc15-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cc15-113">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4cc15-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4cc15-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cc15-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cc15-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4cc15-115">See Also</span></span>  
 [<span data-ttu-id="4cc15-116">Iınstallreferenceıtem arabirimi</span><span class="sxs-lookup"><span data-stu-id="4cc15-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="4cc15-117">Fusıon_ınstall_reference yapısı</span><span class="sxs-lookup"><span data-stu-id="4cc15-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)

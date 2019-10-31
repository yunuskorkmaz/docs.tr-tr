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
ms.openlocfilehash: 014bd4f2b12c84790065f76a67765aaf35e8b2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131678"
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="9134a-102">IInstallReferenceItem::GetReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9134a-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="9134a-103">Bu [IInstallReferenceItem](iinstallreferenceitem-interface.md) nesnesinin temsil ettiği [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) yapısına yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="9134a-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9134a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9134a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9134a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9134a-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="9134a-106">dışı Döndürülen `FUSION_INSTALL_REFERENCE` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9134a-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9134a-107">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9134a-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9134a-108">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9134a-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="9134a-109">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9134a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="9134a-110">`pvReserved`, null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9134a-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9134a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9134a-111">Requirements</span></span>  
 <span data-ttu-id="9134a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9134a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9134a-113">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9134a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9134a-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9134a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9134a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9134a-115">See also</span></span>

- [<span data-ttu-id="9134a-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9134a-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)
- [<span data-ttu-id="9134a-117">FUSION_INSTALL_REFERENCE Yapısı</span><span class="sxs-lookup"><span data-stu-id="9134a-117">FUSION_INSTALL_REFERENCE Structure</span></span>](fusion-install-reference-structure.md)

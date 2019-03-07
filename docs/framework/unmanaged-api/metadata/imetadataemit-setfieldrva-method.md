---
title: IMetaDataEmit::SetFieldRVA Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a38de994575bf0191ff2ab5ce1c7b047540289f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470594"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="d1064-102">IMetaDataEmit::SetFieldRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1064-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="d1064-103">Göreli sanal adres alanının belirtilen belirteci tarafından başvurulan bir genel değişken değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d1064-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1064-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1064-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1064-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1064-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="d1064-106">[in] Hedef alan belirteci.</span><span class="sxs-lookup"><span data-stu-id="d1064-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="d1064-107">[in] Bir kod veya veri alanı adresi.</span><span class="sxs-lookup"><span data-stu-id="d1064-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1064-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1064-108">Requirements</span></span>  
 <span data-ttu-id="d1064-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1064-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1064-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d1064-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1064-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="d1064-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1064-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1064-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1064-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1064-113">See also</span></span>
- [<span data-ttu-id="d1064-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1064-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d1064-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1064-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

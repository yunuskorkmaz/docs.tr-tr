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
ms.openlocfilehash: 4ebde1d506a120a99e1c637c660b45d698994f5a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181681"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="241d2-102">IMetaDataEmit::SetFieldRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="241d2-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="241d2-103">Göreli sanal adres alanının belirtilen belirteci tarafından başvurulan bir genel değişken değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="241d2-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="241d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="241d2-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="241d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="241d2-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="241d2-106">[in] Hedef alan belirteci.</span><span class="sxs-lookup"><span data-stu-id="241d2-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="241d2-107">[in] Bir kod veya veri alanı adresi.</span><span class="sxs-lookup"><span data-stu-id="241d2-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="241d2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="241d2-108">Requirements</span></span>  
 <span data-ttu-id="241d2-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="241d2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="241d2-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="241d2-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="241d2-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="241d2-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="241d2-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="241d2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="241d2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="241d2-113">See also</span></span>

- [<span data-ttu-id="241d2-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="241d2-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="241d2-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="241d2-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

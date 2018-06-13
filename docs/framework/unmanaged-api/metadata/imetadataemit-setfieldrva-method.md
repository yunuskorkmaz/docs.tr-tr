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
ms.openlocfilehash: 0447a44c555e141c96d6a52ba330e181151a7bc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445896"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="7b299-102">IMetaDataEmit::SetFieldRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7b299-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="7b299-103">Göreli sanal adres alanının belirtilen belirtecin tarafından başvurulan genel bir değişken değerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7b299-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b299-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b299-104">Syntax</span></span>  
  
```  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b299-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b299-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="7b299-106">[in] Hedef alan için belirteci.</span><span class="sxs-lookup"><span data-stu-id="7b299-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="7b299-107">[in] Bir kod veya veri alanı adresi.</span><span class="sxs-lookup"><span data-stu-id="7b299-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b299-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b299-108">Requirements</span></span>  
 <span data-ttu-id="7b299-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b299-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b299-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7b299-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b299-111">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7b299-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b299-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b299-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b299-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b299-113">See Also</span></span>  
 [<span data-ttu-id="7b299-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b299-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7b299-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b299-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

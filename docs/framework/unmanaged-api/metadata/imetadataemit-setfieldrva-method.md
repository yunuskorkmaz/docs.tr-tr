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
ms.openlocfilehash: 7648a1b3d219ee5d2b1ddc6b26f7b65c9ac85105
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175648"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="6266e-102">IMetaDataEmit::SetFieldRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6266e-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="6266e-103">Belirtilen belirteç tarafından başvurulan alanın göreli sanal adresi için genel bir değişken değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6266e-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6266e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6266e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6266e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6266e-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="6266e-106">[içinde] Hedef alanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="6266e-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="6266e-107">[içinde] Bir kodun veya veri alanının adresi.</span><span class="sxs-lookup"><span data-stu-id="6266e-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6266e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6266e-108">Requirements</span></span>  
 <span data-ttu-id="6266e-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6266e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6266e-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6266e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6266e-111">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6266e-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6266e-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6266e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6266e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6266e-113">See also</span></span>

- [<span data-ttu-id="6266e-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6266e-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6266e-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6266e-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

---
title: IMetaDataEmit::SetRVA Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
ms.openlocfilehash: fe0b4b7fef0d05c4acc06dad5bc8a4eaf0722c9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175583"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="23309-102">IMetaDataEmit::SetRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23309-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="23309-103">Belirtilen yöntemin göreli sanal adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="23309-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23309-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23309-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23309-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23309-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="23309-106">[içinde] Hedef yöntem veya yöntem uygulaması için belirteç.</span><span class="sxs-lookup"><span data-stu-id="23309-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="23309-107">[içinde] Kodun veya veri alanının adresi.</span><span class="sxs-lookup"><span data-stu-id="23309-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23309-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23309-108">Requirements</span></span>  
 <span data-ttu-id="23309-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23309-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23309-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="23309-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23309-111">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="23309-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23309-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23309-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23309-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23309-113">See also</span></span>

- [<span data-ttu-id="23309-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23309-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="23309-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23309-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

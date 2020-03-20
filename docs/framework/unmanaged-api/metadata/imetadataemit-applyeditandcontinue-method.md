---
title: IMetaDataEmit::ApplyEditAndContinue Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: f876187624d066b9e672fbf44a984d6d02a54c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175882"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="5bcca-102">IMetaDataEmit::ApplyEditAndContinue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bcca-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="5bcca-103">Geçerli derleme kapsamını belirtilen meta verilerde yapılan değişikliklerle güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="5bcca-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bcca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bcca-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bcca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bcca-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="5bcca-106">\[işaretçide\] taşınabilir yürütülebilir (PE) dosyasından delta meta verilerini temsil eden bir [IUnknown](/cpp/atl/iunknown) nesnesine.</span><span class="sxs-lookup"><span data-stu-id="5bcca-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="5bcca-107">Delta meta verileri, modülün gerçek meta verilerinin kopyasında yapılan değişiklikleri içeren meta veri bloğudur.</span><span class="sxs-lookup"><span data-stu-id="5bcca-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bcca-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bcca-108">Requirements</span></span>  
 <span data-ttu-id="5bcca-109">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bcca-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bcca-110">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5bcca-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5bcca-111">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5bcca-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5bcca-112">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bcca-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bcca-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bcca-113">See also</span></span>

- [<span data-ttu-id="5bcca-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bcca-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5bcca-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bcca-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

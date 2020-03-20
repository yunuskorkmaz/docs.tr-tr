---
title: IMetaDataEmit::DefineCustomAttribute Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 9c4ed282e259aa46fc0cb0175214dc51d3d5fbee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175895"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="dfc79-102">IMetaDataEmit::DefineCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfc79-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="dfc79-103">Belirtilen meta veri imzasıyla özel bir öznitelik için, belirtilen nesneye eklenecek bir tanım oluşturur ve bu özel öznitelik tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="dfc79-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfc79-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfc79-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfc79-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="dfc79-106">[içinde] Sahibi öğesinin belirteci.</span><span class="sxs-lookup"><span data-stu-id="dfc79-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="dfc79-107">[içinde] Özel özniteliği tanımlayan belirteç.</span><span class="sxs-lookup"><span data-stu-id="dfc79-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="dfc79-108">[içinde] Özel öznitelik için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfc79-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="dfc79-109">[içinde] Bayt `pCustomAttribute`sayısı.</span><span class="sxs-lookup"><span data-stu-id="dfc79-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="dfc79-110">[çıkış] Atanan `mdCustomAttribute` belirteç.</span><span class="sxs-lookup"><span data-stu-id="dfc79-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc79-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfc79-111">Requirements</span></span>  
 <span data-ttu-id="dfc79-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc79-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dfc79-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dfc79-114">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dfc79-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfc79-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc79-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfc79-116">See also</span></span>

- [<span data-ttu-id="dfc79-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfc79-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dfc79-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfc79-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

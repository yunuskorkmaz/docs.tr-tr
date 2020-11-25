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
ms.openlocfilehash: df9dc1a36a9adcef3f93a9929565cef117e84d75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704233"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="c8223-102">IMetaDataEmit::SetRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8223-102">IMetaDataEmit::SetRVA Method</span></span>

<span data-ttu-id="c8223-103">Belirtilen metodun göreli sanal adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c8223-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8223-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c8223-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8223-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8223-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="c8223-106">'ndaki Hedef Yöntem veya yöntem uygulamasına yönelik belirteç.</span><span class="sxs-lookup"><span data-stu-id="c8223-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="c8223-107">'ndaki Kod veya veri alanının adresi.</span><span class="sxs-lookup"><span data-stu-id="c8223-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8223-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8223-108">Requirements</span></span>  

 <span data-ttu-id="c8223-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8223-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8223-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c8223-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8223-111">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c8223-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8223-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8223-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8223-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8223-113">See also</span></span>

- [<span data-ttu-id="c8223-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8223-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c8223-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8223-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

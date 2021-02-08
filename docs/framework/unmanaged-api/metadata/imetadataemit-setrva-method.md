---
description: ': Imetadatayayma:: SetRVA yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 52294250df2b7a677bb4ecb09ea0a97baca595a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771788"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="08a38-103">IMetaDataEmit::SetRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08a38-103">IMetaDataEmit::SetRVA Method</span></span>

<span data-ttu-id="08a38-104">Belirtilen metodun göreli sanal adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="08a38-104">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a38-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08a38-105">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08a38-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08a38-106">Parameters</span></span>  

 `md`  
 <span data-ttu-id="08a38-107">'ndaki Hedef Yöntem veya yöntem uygulamasına yönelik belirteç.</span><span class="sxs-lookup"><span data-stu-id="08a38-107">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="08a38-108">'ndaki Kod veya veri alanının adresi.</span><span class="sxs-lookup"><span data-stu-id="08a38-108">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08a38-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08a38-109">Requirements</span></span>  

 <span data-ttu-id="08a38-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08a38-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08a38-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="08a38-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08a38-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="08a38-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08a38-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08a38-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a38-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08a38-114">See also</span></span>

- [<span data-ttu-id="08a38-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08a38-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="08a38-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08a38-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

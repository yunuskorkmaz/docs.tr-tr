---
title: IMetaDataEmit::GetTokenFromTypeSpec Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 3a8f369728b8464850259518981bf6690cb17a01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722046"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="0e1be-102">IMetaDataEmit::GetTokenFromTypeSpec Metodu</span><span class="sxs-lookup"><span data-stu-id="0e1be-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>

<span data-ttu-id="0e1be-103">Belirtilen meta veri imzasına sahip tür için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="0e1be-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e1be-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0e1be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e1be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e1be-105">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="0e1be-106">'ndaki Tanımlanmakta olan imza.</span><span class="sxs-lookup"><span data-stu-id="0e1be-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="0e1be-107">'ndaki İçindeki bayt sayısı `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="0e1be-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="0e1be-108">dışı `mdTypeSpec` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="0e1be-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e1be-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e1be-109">Requirements</span></span>  

 <span data-ttu-id="0e1be-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e1be-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e1be-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0e1be-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e1be-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0e1be-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e1be-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e1be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e1be-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e1be-114">See also</span></span>

- [<span data-ttu-id="0e1be-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e1be-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0e1be-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e1be-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

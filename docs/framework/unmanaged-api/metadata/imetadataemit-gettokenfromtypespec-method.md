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
ms.openlocfilehash: 1cd09fe785bb37c892417ddbf1efaaaa90e121bf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009242"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="ff63c-102">IMetaDataEmit::GetTokenFromTypeSpec Metodu</span><span class="sxs-lookup"><span data-stu-id="ff63c-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="ff63c-103">Belirtilen meta veri imzasına sahip tür için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="ff63c-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff63c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ff63c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff63c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff63c-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="ff63c-106">'ndaki Tanımlanmakta olan imza.</span><span class="sxs-lookup"><span data-stu-id="ff63c-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="ff63c-107">'ndaki İçindeki bayt sayısı `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="ff63c-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="ff63c-108">dışı `mdTypeSpec`Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="ff63c-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff63c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff63c-109">Requirements</span></span>  
 <span data-ttu-id="ff63c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff63c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff63c-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ff63c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff63c-112">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ff63c-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff63c-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff63c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff63c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff63c-114">See also</span></span>

- [<span data-ttu-id="ff63c-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff63c-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ff63c-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff63c-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

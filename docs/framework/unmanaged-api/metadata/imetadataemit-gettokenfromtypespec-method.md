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
ms.openlocfilehash: 8c609d730297881c0ac20dca8569f0e9492638e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175726"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="ff283-102">IMetaDataEmit::GetTokenFromTypeSpec Metodu</span><span class="sxs-lookup"><span data-stu-id="ff283-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>
<span data-ttu-id="ff283-103">Belirtilen meta veri imzasına sahip tür için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="ff283-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff283-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff283-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff283-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff283-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="ff283-106">[içinde] İmza tanımlanıyor.</span><span class="sxs-lookup"><span data-stu-id="ff283-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="ff283-107">[içinde] Bayt `pvSig`sayısı.</span><span class="sxs-lookup"><span data-stu-id="ff283-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="ff283-108">[çıkış] Atanan `mdTypeSpec` belirteç.</span><span class="sxs-lookup"><span data-stu-id="ff283-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff283-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff283-109">Requirements</span></span>  
 <span data-ttu-id="ff283-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff283-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff283-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff283-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff283-112">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ff283-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff283-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff283-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff283-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff283-114">See also</span></span>

- [<span data-ttu-id="ff283-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff283-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ff283-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff283-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

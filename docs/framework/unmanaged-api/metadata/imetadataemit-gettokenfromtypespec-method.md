---
description: ': Imetadatayayma:: GetTokenFromTypeSpec metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 09f7133af9b9d912b03cdc1c93744ee260c69169
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728242"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="ae9c2-103">IMetaDataEmit::GetTokenFromTypeSpec Metodu</span><span class="sxs-lookup"><span data-stu-id="ae9c2-103">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>

<span data-ttu-id="ae9c2-104">Belirtilen meta veri imzasına sahip tür için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="ae9c2-104">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae9c2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae9c2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae9c2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae9c2-106">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="ae9c2-107">'ndaki Tanımlanmakta olan imza.</span><span class="sxs-lookup"><span data-stu-id="ae9c2-107">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="ae9c2-108">'ndaki İçindeki bayt sayısı `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="ae9c2-108">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="ae9c2-109">dışı `mdTypeSpec` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="ae9c2-109">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae9c2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae9c2-110">Requirements</span></span>  

 <span data-ttu-id="ae9c2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae9c2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae9c2-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ae9c2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae9c2-113">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ae9c2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae9c2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae9c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae9c2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae9c2-115">See also</span></span>

- [<span data-ttu-id="ae9c2-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae9c2-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ae9c2-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae9c2-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

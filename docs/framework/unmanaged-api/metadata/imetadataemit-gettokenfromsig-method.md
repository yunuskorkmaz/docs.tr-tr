---
title: IMetaDataEmit::GetTokenFromSig Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
ms.openlocfilehash: f1262181fa745e1b6d3fc48a4ad728c1020705b5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434321"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="ae8e0-102">IMetaDataEmit::GetTokenFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="ae8e0-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="ae8e0-103">Belirtilen meta veri imzası için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="ae8e0-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae8e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae8e0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (   
    [in]  PCCOR_SIGNATURE pvSig,   
    [in]  ULONG       cbSig,   
    [out] mdSignature *pmsig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae8e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae8e0-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="ae8e0-106">'ndaki Kalıcı yapılacak ve depolanacak imza.</span><span class="sxs-lookup"><span data-stu-id="ae8e0-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="ae8e0-107">'ndaki `pvSig`bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="ae8e0-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="ae8e0-108">dışı `mdSignature` belirteci atandı.</span><span class="sxs-lookup"><span data-stu-id="ae8e0-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae8e0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae8e0-109">Requirements</span></span>  
 <span data-ttu-id="ae8e0-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae8e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae8e0-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ae8e0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae8e0-112">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ae8e0-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae8e0-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae8e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae8e0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae8e0-114">See also</span></span>

- [<span data-ttu-id="ae8e0-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae8e0-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ae8e0-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae8e0-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

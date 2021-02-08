---
description: ': Imetadatayayma:: GetTokenFromSig yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3b9b38389a2bf78a65baa2cf96e3a422c54d0bcb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783930"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="0d7c9-103">IMetaDataEmit::GetTokenFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="0d7c9-103">IMetaDataEmit::GetTokenFromSig Method</span></span>

<span data-ttu-id="0d7c9-104">Belirtilen meta veri imzası için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="0d7c9-104">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d7c9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d7c9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d7c9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d7c9-106">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="0d7c9-107">'ndaki Kalıcı yapılacak ve depolanacak imza.</span><span class="sxs-lookup"><span data-stu-id="0d7c9-107">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="0d7c9-108">'ndaki İçindeki bayt sayısı `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="0d7c9-108">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="0d7c9-109">dışı `mdSignature` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="0d7c9-109">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d7c9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d7c9-110">Requirements</span></span>  

 <span data-ttu-id="0d7c9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d7c9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d7c9-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0d7c9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d7c9-113">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0d7c9-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d7c9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d7c9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7c9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d7c9-115">See also</span></span>

- [<span data-ttu-id="0d7c9-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d7c9-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0d7c9-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d7c9-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

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
ms.openlocfilehash: 740dad54bc3a79ff546176abdc35487d89ed8f44
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009255"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="aa0c7-102">IMetaDataEmit::GetTokenFromSig Metodu</span><span class="sxs-lookup"><span data-stu-id="aa0c7-102">IMetaDataEmit::GetTokenFromSig Method</span></span>
<span data-ttu-id="aa0c7-103">Belirtilen meta veri imzası için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="aa0c7-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa0c7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aa0c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa0c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa0c7-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="aa0c7-106">'ndaki Kalıcı yapılacak ve depolanacak imza.</span><span class="sxs-lookup"><span data-stu-id="aa0c7-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="aa0c7-107">'ndaki İçindeki bayt sayısı `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="aa0c7-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="aa0c7-108">dışı `mdSignature`Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="aa0c7-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa0c7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa0c7-109">Requirements</span></span>  
 <span data-ttu-id="aa0c7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa0c7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa0c7-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="aa0c7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa0c7-112">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="aa0c7-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa0c7-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa0c7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa0c7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa0c7-114">See also</span></span>

- [<span data-ttu-id="aa0c7-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa0c7-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="aa0c7-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa0c7-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

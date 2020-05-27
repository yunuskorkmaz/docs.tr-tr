---
title: IMetaDataEmit::DefineUserString Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: def77bb64e21b1421983cf263d488ecc1ddb9452
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009331"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="95868-102">IMetaDataEmit::DefineUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95868-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="95868-103">Belirtilen sabit dize için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="95868-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95868-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="95868-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95868-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95868-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="95868-106">'ndaki Depolanacak Kullanıcı dizesi.</span><span class="sxs-lookup"><span data-stu-id="95868-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="95868-107">'ndaki İçindeki geniş karakterlerin sayısı `szString` .</span><span class="sxs-lookup"><span data-stu-id="95868-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="95868-108">dışı Atanan dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="95868-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95868-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95868-109">Requirements</span></span>  
 <span data-ttu-id="95868-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95868-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95868-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="95868-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95868-112">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="95868-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95868-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95868-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95868-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95868-114">See also</span></span>

- [<span data-ttu-id="95868-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95868-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="95868-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95868-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

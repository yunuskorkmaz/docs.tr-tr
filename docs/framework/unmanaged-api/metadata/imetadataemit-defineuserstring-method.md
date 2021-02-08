---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineUserString yöntemi'
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
ms.openlocfilehash: 0d1c376e3f121d35cb9f6c08d7013a3913a8bd49
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784008"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="2fbd7-103">IMetaDataEmit::DefineUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fbd7-103">IMetaDataEmit::DefineUserString Method</span></span>

<span data-ttu-id="2fbd7-104">Belirtilen sabit dize için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="2fbd7-104">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fbd7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fbd7-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fbd7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2fbd7-106">Parameters</span></span>  

 `szString`  
 <span data-ttu-id="2fbd7-107">'ndaki Depolanacak Kullanıcı dizesi.</span><span class="sxs-lookup"><span data-stu-id="2fbd7-107">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="2fbd7-108">'ndaki İçindeki geniş karakterlerin sayısı `szString` .</span><span class="sxs-lookup"><span data-stu-id="2fbd7-108">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="2fbd7-109">dışı Atanan dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="2fbd7-109">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fbd7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fbd7-110">Requirements</span></span>  

 <span data-ttu-id="2fbd7-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fbd7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fbd7-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2fbd7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2fbd7-113">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2fbd7-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fbd7-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fbd7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fbd7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fbd7-115">See also</span></span>

- [<span data-ttu-id="2fbd7-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fbd7-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2fbd7-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fbd7-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

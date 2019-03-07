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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 820b0c464f591ca71072d35886a910f5409f654e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478303"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="a7c94-102">IMetaDataEmit::DefineUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7c94-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="a7c94-103">Bir meta veri için belirtilen değişmez değer dize belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="a7c94-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c94-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7c94-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7c94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7c94-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="a7c94-106">[in] Depolamak için kullanıcı dizesi.</span><span class="sxs-lookup"><span data-stu-id="a7c94-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="a7c94-107">[in] Geniş karakter sayısı `szString`.</span><span class="sxs-lookup"><span data-stu-id="a7c94-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="a7c94-108">[out] Atanan dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="a7c94-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7c94-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7c94-109">Requirements</span></span>  
 <span data-ttu-id="a7c94-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7c94-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7c94-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a7c94-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7c94-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="a7c94-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7c94-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c94-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c94-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7c94-114">See also</span></span>
- [<span data-ttu-id="a7c94-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7c94-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a7c94-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7c94-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

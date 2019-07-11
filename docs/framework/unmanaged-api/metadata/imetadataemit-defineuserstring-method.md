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
ms.openlocfilehash: 25e35fd9afd2ce4dc60e23ccd64e0630a008bf39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777427"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="bf164-102">IMetaDataEmit::DefineUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf164-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="bf164-103">Bir meta veri için belirtilen değişmez değer dize belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="bf164-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf164-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf164-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf164-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf164-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="bf164-106">[in] Depolamak için kullanıcı dizesi.</span><span class="sxs-lookup"><span data-stu-id="bf164-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="bf164-107">[in] Geniş karakter sayısı `szString`.</span><span class="sxs-lookup"><span data-stu-id="bf164-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="bf164-108">[out] Atanan dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="bf164-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf164-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf164-109">Requirements</span></span>  
 <span data-ttu-id="bf164-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf164-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf164-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bf164-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf164-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="bf164-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf164-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf164-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf164-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf164-114">See also</span></span>

- [<span data-ttu-id="bf164-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf164-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bf164-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf164-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

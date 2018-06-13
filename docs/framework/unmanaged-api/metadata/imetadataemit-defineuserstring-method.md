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
ms.openlocfilehash: 09f2e166072d140fe00fe8ecaee318051953939d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444659"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="a2856-102">IMetaDataEmit::DefineUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2856-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="a2856-103">Bir meta veri için belirtilen değişmez değer dize belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="a2856-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2856-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2856-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2856-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2856-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="a2856-106">[in] Depolamak için kullanıcı dizesi.</span><span class="sxs-lookup"><span data-stu-id="a2856-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="a2856-107">[in] Geniş karakter sayısı `szString`.</span><span class="sxs-lookup"><span data-stu-id="a2856-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="a2856-108">[out] Atanan dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="a2856-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2856-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2856-109">Requirements</span></span>  
 <span data-ttu-id="a2856-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2856-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2856-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2856-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2856-112">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a2856-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2856-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2856-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2856-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2856-114">See Also</span></span>  
 [<span data-ttu-id="a2856-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2856-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a2856-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2856-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

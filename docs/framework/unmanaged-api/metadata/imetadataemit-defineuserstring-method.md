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
ms.openlocfilehash: f24dd3864be1bda454ac5e863f3fa2caf736bda9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215228"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="c5495-102">IMetaDataEmit::DefineUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5495-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="c5495-103">Bir meta veri için belirtilen değişmez değer dize belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="c5495-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5495-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5495-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5495-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5495-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="c5495-106">[in] Depolamak için kullanıcı dizesi.</span><span class="sxs-lookup"><span data-stu-id="c5495-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="c5495-107">[in] Geniş karakter sayısı `szString`.</span><span class="sxs-lookup"><span data-stu-id="c5495-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="c5495-108">[out] Atanan dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="c5495-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5495-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5495-109">Requirements</span></span>  
 <span data-ttu-id="c5495-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5495-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5495-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c5495-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5495-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="c5495-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c5495-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c5495-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5495-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5495-114">See also</span></span>

- [<span data-ttu-id="c5495-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5495-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c5495-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5495-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)

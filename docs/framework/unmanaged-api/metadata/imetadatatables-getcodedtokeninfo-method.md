---
title: IMetaDataTables::GetCodedTokenInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 153aa7d6b8c35129638de3d47ffa6aff72f550c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130708"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="bed3e-102">IMetaDataTables::GetCodedTokenInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="bed3e-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="bed3e-103">Belirteçlerin belirtilen satır dizini ile ilişkili bir diziye bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="bed3e-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bed3e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bed3e-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bed3e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bed3e-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="bed3e-106">[in] Döndürülecek kodlanmış Belirtecin türü.</span><span class="sxs-lookup"><span data-stu-id="bed3e-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bed3e-107">[out] Bir işaretçisi uzunluğuna `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="bed3e-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="bed3e-108">[out] Verilen belirteçlerin listesi içeren bir dizi işaretçisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bed3e-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="bed3e-109">[out] Bir işaretçi işaretçisi belirteç adını `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="bed3e-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bed3e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bed3e-110">Requirements</span></span>  
 <span data-ttu-id="bed3e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bed3e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bed3e-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bed3e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bed3e-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="bed3e-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="bed3e-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bed3e-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bed3e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bed3e-115">See also</span></span>

- [<span data-ttu-id="bed3e-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bed3e-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="bed3e-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bed3e-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

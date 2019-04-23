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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130708"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="1caed-102">IMetaDataTables::GetCodedTokenInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="1caed-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="1caed-103">Belirteçlerin belirtilen satır dizini ile ilişkili bir diziye bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="1caed-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1caed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1caed-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1caed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1caed-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="1caed-106">[in] Döndürülecek kodlanmış Belirtecin türü.</span><span class="sxs-lookup"><span data-stu-id="1caed-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="1caed-107">[out] Bir işaretçisi uzunluğuna `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="1caed-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="1caed-108">[out] Verilen belirteçlerin listesi içeren bir dizi işaretçisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1caed-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="1caed-109">[out] Bir işaretçi işaretçisi belirteç adını `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="1caed-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1caed-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1caed-110">Requirements</span></span>  
 <span data-ttu-id="1caed-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1caed-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1caed-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1caed-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1caed-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1caed-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1caed-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1caed-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1caed-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1caed-115">See also</span></span>

- [<span data-ttu-id="1caed-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1caed-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1caed-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1caed-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

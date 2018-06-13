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
ms.openlocfilehash: a7a36d14b67efb3934089dc16de41a3b80ea0c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447996"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="0b441-102">IMetaDataTables::GetCodedTokenInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="0b441-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="0b441-103">Belirtilen satır dizini ile ilişkili belirteçleri dizisi için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="0b441-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b441-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b441-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b441-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b441-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="0b441-106">[in] Döndürülecek kodlanmış belirteci türü.</span><span class="sxs-lookup"><span data-stu-id="0b441-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="0b441-107">[out] Bir işaretçi uzunluğu `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="0b441-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="0b441-108">[out] Belirteçleri listesini içeren bir dizi için bir işaretçi bir işaretçi döndürdü.</span><span class="sxs-lookup"><span data-stu-id="0b441-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="0b441-109">[out] Belirtecin adını gösteren bir işaretçi bir işaretçi `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="0b441-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b441-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b441-110">Requirements</span></span>  
 <span data-ttu-id="0b441-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b441-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b441-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0b441-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b441-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0b441-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b441-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b441-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b441-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b441-115">See Also</span></span>  
 [<span data-ttu-id="0b441-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b441-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="0b441-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b441-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

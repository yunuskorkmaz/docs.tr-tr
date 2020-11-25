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
ms.openlocfilehash: b79ac7f71ec0551336298a90829e1f37e2e30b20
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711093"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="6897b-102">IMetaDataTables::GetCodedTokenInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="6897b-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>

<span data-ttu-id="6897b-103">Belirtilen satır diziniyle ilişkili bir belirteç dizisine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6897b-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6897b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6897b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6897b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6897b-105">Parameters</span></span>  

 `ixCdTkn`  
 <span data-ttu-id="6897b-106">'ndaki Döndürülecek kodlanmış belirtecin türü.</span><span class="sxs-lookup"><span data-stu-id="6897b-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6897b-107">dışı Uzunluğuna yönelik bir işaretçi `ppTokens` .</span><span class="sxs-lookup"><span data-stu-id="6897b-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="6897b-108">dışı Döndürülen belirteçlerin listesini içeren bir dizi işaretçisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6897b-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="6897b-109">dışı İçindeki belirtecin adı için bir işaretçiye yönelik işaretçi `ixCdTkn` .</span><span class="sxs-lookup"><span data-stu-id="6897b-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6897b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6897b-110">Requirements</span></span>  

 <span data-ttu-id="6897b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6897b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6897b-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6897b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6897b-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6897b-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6897b-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6897b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6897b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6897b-115">See also</span></span>

- [<span data-ttu-id="6897b-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6897b-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="6897b-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6897b-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

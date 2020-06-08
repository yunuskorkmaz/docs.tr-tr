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
ms.openlocfilehash: 8ab16ad5b2b2838125e07511ef47be737f40671c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501215"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="6626a-102">IMetaDataTables::GetCodedTokenInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="6626a-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="6626a-103">Belirtilen satır diziniyle ilişkili bir belirteç dizisine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6626a-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6626a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6626a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6626a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6626a-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="6626a-106">'ndaki Döndürülecek kodlanmış belirtecin türü.</span><span class="sxs-lookup"><span data-stu-id="6626a-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6626a-107">dışı Uzunluğuna yönelik bir işaretçi `ppTokens` .</span><span class="sxs-lookup"><span data-stu-id="6626a-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="6626a-108">dışı Döndürülen belirteçlerin listesini içeren bir dizi işaretçisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6626a-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="6626a-109">dışı İçindeki belirtecin adı için bir işaretçiye yönelik işaretçi `ixCdTkn` .</span><span class="sxs-lookup"><span data-stu-id="6626a-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6626a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6626a-110">Requirements</span></span>  
 <span data-ttu-id="6626a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6626a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6626a-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6626a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6626a-113">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6626a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6626a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6626a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6626a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6626a-115">See also</span></span>

- [<span data-ttu-id="6626a-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6626a-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="6626a-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6626a-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

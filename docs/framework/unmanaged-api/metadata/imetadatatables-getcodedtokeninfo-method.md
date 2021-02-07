---
description: ': IMetaDataTables:: GetCodedTokenInfo metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 982a13636d8b4572113038eaa658158e6c2ca966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688292"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="ebf0c-103">IMetaDataTables::GetCodedTokenInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="ebf0c-103">IMetaDataTables::GetCodedTokenInfo Method</span></span>

<span data-ttu-id="ebf0c-104">Belirtilen satır diziniyle ilişkili bir belirteç dizisine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ebf0c-104">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf0c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ebf0c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebf0c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ebf0c-106">Parameters</span></span>  

 `ixCdTkn`  
 <span data-ttu-id="ebf0c-107">'ndaki Döndürülecek kodlanmış belirtecin türü.</span><span class="sxs-lookup"><span data-stu-id="ebf0c-107">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ebf0c-108">dışı Uzunluğuna yönelik bir işaretçi `ppTokens` .</span><span class="sxs-lookup"><span data-stu-id="ebf0c-108">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="ebf0c-109">dışı Döndürülen belirteçlerin listesini içeren bir dizi işaretçisine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ebf0c-109">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="ebf0c-110">dışı İçindeki belirtecin adı için bir işaretçiye yönelik işaretçi `ixCdTkn` .</span><span class="sxs-lookup"><span data-stu-id="ebf0c-110">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf0c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebf0c-111">Requirements</span></span>  

 <span data-ttu-id="ebf0c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf0c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf0c-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ebf0c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebf0c-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ebf0c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebf0c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf0c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf0c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebf0c-116">See also</span></span>

- [<span data-ttu-id="ebf0c-117">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebf0c-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ebf0c-118">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebf0c-118">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

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
ms.openlocfilehash: 64c70fe0b657047ae35dccb763fa57120403deef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177148"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="db178-102">IMetaDataTables::GetCodedTokenInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="db178-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="db178-103">Belirtilen satır dizini ile ilişkili belirteçleri bir dizi için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="db178-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db178-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db178-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db178-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db178-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="db178-106">[içinde] İade etmek için kodlanmış bir belirteç türü.</span><span class="sxs-lookup"><span data-stu-id="db178-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="db178-107">[çıkış] Uzunluğuna işareteden `ppTokens`bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db178-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="db178-108">[çıkış] Döndürülen belirteçlerin listesini içeren bir dizi için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db178-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="db178-109">[çıkış] 'deki `ixCdTkn`belirteç adına işaretçi için bir işaretçi</span><span class="sxs-lookup"><span data-stu-id="db178-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db178-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db178-110">Requirements</span></span>  
 <span data-ttu-id="db178-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db178-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db178-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db178-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db178-113">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="db178-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db178-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db178-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db178-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db178-115">See also</span></span>

- [<span data-ttu-id="db178-116">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db178-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="db178-117">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db178-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

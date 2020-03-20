---
title: IMetaDataTables::GetRow Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177113"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="e5a6e-102">IMetaDataTables::GetRow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5a6e-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="e5a6e-103">Belirtilen satır dizinindeki satırı, belirtilen tablo dizinindeki tabloda alır.</span><span class="sxs-lookup"><span data-stu-id="e5a6e-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5a6e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5a6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e5a6e-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="e5a6e-106">[içinde] Satırın alınacağı tablonun dizini.</span><span class="sxs-lookup"><span data-stu-id="e5a6e-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="e5a6e-107">[içinde] Almak için satır ın dizini.</span><span class="sxs-lookup"><span data-stu-id="e5a6e-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="e5a6e-108">[çıkış] Satıra işaretçi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e5a6e-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5a6e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5a6e-109">Remarks</span></span>  

  <span data-ttu-id="e5a6e-110">Tutarlı sonuçlar döndürmediği için bu yöntemin kullanılmasını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="e5a6e-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e5a6e-111">GUID tablosu hakkında bilgi için, "Partition II: Metadata Definition and Semantics" başta olmak üzere Ortak Dil Altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="e5a6e-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e5a6e-112">Dokümantasyon online olarak mevcuttur; bkz. [ECMA C# ve Ortak Dil Altyapı Standartları](../../../standard/components.md#applicable-standards) ve Standart [ECMA-335 - Ortak Dil Altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="e5a6e-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5a6e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5a6e-113">Requirements</span></span>  
 <span data-ttu-id="e5a6e-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5a6e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5a6e-115">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5a6e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5a6e-116">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e5a6e-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e5a6e-117">**.NET Çerçeve Sürümleri**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5a6e-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a6e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5a6e-118">See also</span></span>

- [<span data-ttu-id="e5a6e-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5a6e-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="e5a6e-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5a6e-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

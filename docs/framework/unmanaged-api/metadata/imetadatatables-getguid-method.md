---
title: IMetaDataTables::GetGuid Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175284"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="82c26-102">IMetaDataTables::GetGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="82c26-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="82c26-103">Belirtilen dizindeki satırdan bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="82c26-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82c26-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82c26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82c26-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="82c26-106">[içinde] GUID almak için satır ın dizin.</span><span class="sxs-lookup"><span data-stu-id="82c26-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="82c26-107">[çıkış] GUID için bir işaretçi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="82c26-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82c26-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82c26-108">Remarks</span></span>  

  <span data-ttu-id="82c26-109">Tutarlı sonuçlar döndürmediği için bu yöntemin kullanılmasını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="82c26-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="82c26-110">GUID tablosu hakkında bilgi için, "Partition II: Metadata Definition and Semantics" başta olmak üzere Ortak Dil Altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="82c26-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="82c26-111">Dokümantasyon online olarak mevcuttur; bkz. [ECMA C# ve Ortak Dil Altyapı Standartları](../../../standard/components.md#applicable-standards) ve Standart [ECMA-335 - Ortak Dil Altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="82c26-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82c26-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82c26-112">Requirements</span></span>  
 <span data-ttu-id="82c26-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82c26-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82c26-114">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="82c26-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82c26-115">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="82c26-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82c26-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82c26-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c26-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82c26-117">See also</span></span>

- [<span data-ttu-id="82c26-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82c26-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="82c26-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82c26-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)

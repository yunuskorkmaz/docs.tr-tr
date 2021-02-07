---
description: ': IMetaDataTables:: GetTableIndex metodu hakkında daha fazla bilgi edinin'
title: IMetaDataTables::GetTableIndex Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
ms.openlocfilehash: d42a42a1a19a67fada17bbe1016f7e324cd1c287
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687733"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="8bd6d-103">IMetaDataTables::GetTableIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8bd6d-103">IMetaDataTables::GetTableIndex Method</span></span>

<span data-ttu-id="8bd6d-104">Belirtilen belirteç tarafından başvurulan tablonun dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="8bd6d-104">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bd6d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8bd6d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bd6d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8bd6d-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="8bd6d-107">'ndaki Tabloya başvuran belirteç.</span><span class="sxs-lookup"><span data-stu-id="8bd6d-107">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="8bd6d-108">dışı Başvurulan tablo için döndürülen dizine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8bd6d-108">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bd6d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bd6d-109">Remarks</span></span>  

 <span data-ttu-id="8bd6d-110">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="8bd6d-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="8bd6d-111">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="8bd6d-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="8bd6d-112">Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="8bd6d-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bd6d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bd6d-113">Requirements</span></span>  

 <span data-ttu-id="8bd6d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bd6d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bd6d-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8bd6d-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8bd6d-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8bd6d-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8bd6d-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bd6d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bd6d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bd6d-118">See also</span></span>

- [<span data-ttu-id="8bd6d-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bd6d-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="8bd6d-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bd6d-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

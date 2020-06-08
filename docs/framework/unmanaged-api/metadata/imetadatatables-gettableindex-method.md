---
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
ms.openlocfilehash: 3638ab12fc311ece9f24608cbb36219e10f01f2d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501187"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="41b0a-102">IMetaDataTables::GetTableIndex Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41b0a-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="41b0a-103">Belirtilen belirteç tarafından başvurulan tablonun dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="41b0a-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41b0a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="41b0a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41b0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41b0a-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="41b0a-106">'ndaki Tabloya başvuran belirteç.</span><span class="sxs-lookup"><span data-stu-id="41b0a-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="41b0a-107">dışı Başvurulan tablo için döndürülen dizine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="41b0a-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41b0a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41b0a-108">Remarks</span></span>  
 <span data-ttu-id="41b0a-109">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="41b0a-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="41b0a-110">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="41b0a-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="41b0a-111">Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="41b0a-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41b0a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41b0a-112">Requirements</span></span>  
 <span data-ttu-id="41b0a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41b0a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41b0a-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="41b0a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="41b0a-115">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="41b0a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="41b0a-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41b0a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41b0a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41b0a-117">See also</span></span>

- [<span data-ttu-id="41b0a-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41b0a-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="41b0a-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41b0a-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

---
description: ': IMetaDataTables:: GetNextGuid metodu hakkında daha fazla bilgi edinin'
title: IMetaDataTables::GetNextGuid Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
ms.openlocfilehash: 86c248bf503410a07fc0b4cf622694c4da213c34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688110"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="ccd1e-103">IMetaDataTables::GetNextGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="ccd1e-103">IMetaDataTables::GetNextGuid Method</span></span>

<span data-ttu-id="ccd1e-104">Geçerli tablo sütunundaki sonraki GUID değerinin dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="ccd1e-104">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd1e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccd1e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccd1e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccd1e-106">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="ccd1e-107">'ndaki Bir GUID tablo sütunundaki dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="ccd1e-107">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="ccd1e-108">dışı Sonraki GUID değerinin dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccd1e-108">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccd1e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccd1e-109">Remarks</span></span>  

  <span data-ttu-id="ccd1e-110">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="ccd1e-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="ccd1e-111">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="ccd1e-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="ccd1e-112">Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="ccd1e-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccd1e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccd1e-113">Requirements</span></span>  

 <span data-ttu-id="ccd1e-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccd1e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccd1e-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ccd1e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccd1e-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ccd1e-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccd1e-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccd1e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccd1e-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccd1e-118">See also</span></span>

- [<span data-ttu-id="ccd1e-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccd1e-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ccd1e-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccd1e-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

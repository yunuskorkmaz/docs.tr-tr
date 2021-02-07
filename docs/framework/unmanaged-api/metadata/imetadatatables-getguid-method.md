---
description: ': IMetaDataTables:: GetGuid metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9c3b8b11bb2f6a1abc3c55d953e1cbfbd7ee8622
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688175"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="a27ff-103">IMetaDataTables::GetGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="a27ff-103">IMetaDataTables::GetGuid Method</span></span>

<span data-ttu-id="a27ff-104">Belirtilen dizindeki satırdan bir GUID alır.</span><span class="sxs-lookup"><span data-stu-id="a27ff-104">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a27ff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a27ff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a27ff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a27ff-106">Parameters</span></span>  

 `ixGuid`  
 <span data-ttu-id="a27ff-107">'ndaki GUID 'nin alınacağı satırın dizini.</span><span class="sxs-lookup"><span data-stu-id="a27ff-107">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="a27ff-108">dışı GUID işaretçisinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a27ff-108">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a27ff-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a27ff-109">Remarks</span></span>  

  <span data-ttu-id="a27ff-110">Tutarlı sonuçlar döndürmediğinden bu yöntemin kullanımını önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="a27ff-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="a27ff-111">GUID tablosu hakkında daha fazla bilgi için, bkz. ortak dil altyapısı (CLı) belgeleri, özellikle "Bölüm II: meta veri tanımı ve semantiği".</span><span class="sxs-lookup"><span data-stu-id="a27ff-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="a27ff-112">Belgeler çevrimiçi olarak kullanılabilir; bkz. [ecma C# ve ortak dil altyapısı standartları](../../../standard/components.md#applicable-standards) ve [standart ECMA-335-ortak DIL altyapısı (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="a27ff-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a27ff-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a27ff-113">Requirements</span></span>  

 <span data-ttu-id="a27ff-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a27ff-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a27ff-115">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a27ff-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a27ff-116">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a27ff-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a27ff-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a27ff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27ff-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a27ff-118">See also</span></span>

- [<span data-ttu-id="a27ff-119">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a27ff-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="a27ff-120">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a27ff-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)

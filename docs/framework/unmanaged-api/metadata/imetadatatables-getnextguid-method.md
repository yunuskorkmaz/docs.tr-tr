---
title: IMetaDataTables::GetNextGuid Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d3585778d9076cb313ffed69a0e126891c4ce49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="bb00a-102">IMetaDataTables::GetNextGuid Metodu</span><span class="sxs-lookup"><span data-stu-id="bb00a-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="bb00a-103">Geçerli bir tablo sütununda sonraki GUID değeri dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="bb00a-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb00a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb00a-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb00a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb00a-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="bb00a-106">[in] Bir GUID tablo sütunu dizin değeri.</span><span class="sxs-lookup"><span data-stu-id="bb00a-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="bb00a-107">[out] Sonraki GUID değeri dizini için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb00a-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb00a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb00a-108">Remarks</span></span>  
 <span data-ttu-id="bb00a-109">Tutarlı sonuçlar döndürmüyor olduğundan, bu yöntemin kullanılması önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="bb00a-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="bb00a-110">GUID tablosu hakkında daha fazla bilgi için özellikle "Bölüm II: meta veri tanım ve semantiği" ortak dil altyapısı (CLI) belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="bb00a-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="bb00a-111">Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="bb00a-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb00a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb00a-112">Requirements</span></span>  
 <span data-ttu-id="bb00a-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb00a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb00a-114">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bb00a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb00a-115">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="bb00a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb00a-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb00a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb00a-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb00a-117">See Also</span></span>  
 [<span data-ttu-id="bb00a-118">IMetaDataTables Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb00a-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="bb00a-119">IMetaDataTables2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb00a-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
